# Data Engineering Nanodegree - Part 3 - Data Lakes with Spark


## Data Engineering


### Data Lakes With Spark


#### Module 4


##### Data Wrangling With Spark

<p><details><summary>Q: In which language is Spark written?</summary><b>Answer</b>: Scala

</details></p>

<p><details><summary>Q: How is it possible that Spark programs can be written in Python if Python is not a functional programming language?</summary><b>Answer</b>: <ul><li>The PySpark API allows you to write programs in <br>Spark and ensures that your code uses functional programming practices.&nbsp;</li><li>&nbsp;Underneath the hood, the Python code uses py4j to make calls to the Java<br> Virtual Machine (JVM).</li></ul>

</details></p>

<p><details><summary>Q: What are <b>resilient distributed datasets </b>(<b>RDD</b>'s)?</summary><b>Answer</b>: <ul><li>RDDs are exactly what they say they are: fault-tolerant datasets distributed across a cluster. </li><li>This is how Spark stores data.</li></ul>

</details></p>


##### The Power Of Spark

<p><details><summary>Q: What's the CPU?</summary><b>Answer</b>: The CPU is the "brain" of the computer.&nbsp;

<b><i>Remarks</i></b>: <ul><li>Every process on your computer is eventually handled by your CPU.&nbsp;</li><li>This includes calculations and also instructions for the other components of the compute.</li></ul>

</details></p>

<p><details><summary>Q: What's the memory (RAM)?</summary><b>Answer</b>: <ul><li>When your program runs, data gets temporarily stored in memory before getting sent to the CPU.&nbsp;</li><li>Memory is <em>ephemeral</em> storage - when your computer shuts down, the data in the memory is lost.</li></ul>

</details></p>

<p><details><summary>Q: What's the storage (SSD or Magnetic Disk)?</summary><b>Answer</b>: <ul><li>Storage is used for keeping data over long periods of time.&nbsp;</li><li>When a 
program runs, the CPU will direct the memory to temporarily load data 
from long-term storage.</li></ul>

</details></p>

<p><details><summary>Q: What's the Network (LAN or Internet)?</summary><b>Answer</b>: <ul><li>Network is the gateway for anything that you need that isn't stored on 
your computer.&nbsp;</li><li>The network could connect to other computers in the same 
room (a Local Area Network) or to a computer on the other side of the 
world, connected over the internet.</li></ul>

</details></p>

<p><details><summary>Q: Rank the following hardware components in order from fastests to slowest: Memory, Disk Storage, Network, CPU.</summary><b>Answer</b>: <ol><li>CPU</li><li>Memory (RAM)</li><li>Disk Storage (SSD)</li><li>Network</li></ol>

<b><i>Remarks</i></b>: CPU operations are fastest. Operations in memory (RAM) are the second 
fastest. Then comes hard disk storage and finally transferring data 
across a network. Keep these relative speeds in mind. They'll help you 
understand the constraints when working with big data.

</details></p>

<p><details><summary>Q: What are the functions of the <b>CPU</b>?</summary><b>Answer</b>: <ul><li>It has a few different functions including directing other 
components of a computer as well as running mathematical calculations.&nbsp;</li><li>The CPU can also store small amounts of data inside itself in what are 
called <strong>registers</strong>.</li></ul>

<b><i>Example</i></b>: <ul><li>For example, say you write a program that reads in a 40 MB data file 
and then analyzes the file.&nbsp;</li><li>When you execute the code, the instructions 
are loaded into the CPU.&nbsp;</li><li>The CPU then instructs the computer to take the
 40 MB from disk and store the data in memory (RAM).&nbsp;</li><li>If you want to sum a
 column of data, then the CPU will essentially take two numbers at a 
time and sum them together.&nbsp;</li><li>The accumulation of the sum needs to be 
stored somewhere while the CPU grabs the next number. This cumulative sum will be stored in a register.&nbsp;</li><li>The registers make 
computations more efficient: the registers avoid having to send data 
unnecessarily back and forth between memory (RAM) and the CPU.</li></ul>

</details></p>

<p><details><summary>Q: What does it mean for a CPU to be 2.5 Gigahertz?</summary><b>Answer</b>: It means that the CPU processes 2.5 billion operations per second.

</details></p>

<p><details><summary>Q: Knowing that tweets create approximately 104 billion bytes of data per 
day, how long would it take the 2.5 GigaHertz CPU to analyze a full day 
of tweets?</summary><b>Answer</b>: 104 billion bytes * (1 second / 20 billion bytes) = 5.2 seconds

<b><i>Remarks</i></b>: <div><ul><li>Twitter generates about 6,000 tweets per second, and each tweet 
contains 200 bytes. So in one day, Twitter generates data on the order 
of:</li><li>(6000 tweets / second) x (86400 seconds / day) x (200 bytes / tweet) = 104 billion bytes / day</li></ul></div>


</details></p>

<p><details><summary>Q: What are the limitations of memory (RAM)?</summary><b>Answer</b>: <ol><li>It's relatively expensive</li><li>It's ephemeral (data stored in RAM gets erased when the computer shuts down)</li></ol>

<b><i>Remarks</i></b>: However, it is efficient: operations in RAM are relatively fast compared to reading and writing from disk or moving data across a network.

</details></p>

<p><details><summary>Q: What is <b>shuffling</b>?</summary><b>Answer</b>: Moving data back and forth between different nodes of a cluster.

<b><i>Remarks</i></b>: Since this is very time expensive, Spark tries to reduce shuffling.

</details></p>

<p><details><summary>Q: List the key ratios of processing speed between the major hardware components.</summary><b>Answer</b>: <ol><li>CPU: 200x faster than memory</li><li>Memory: 15x faster than SSD</li><li>SSD: 20x faster than network</li></ol>

</details></p>

<p><details><summary>Q: What's a difference between <b>parallel computing</b> and <b>distributed computing</b>?</summary><b>Answer</b>: <ul><li>At a high level, distributed computing implies multiple CPUs each with 
its own memory. </li><li>Parallel computing uses multiple CPUs sharing the same 
memory.</li></ul>

</details></p>

<p><details><summary>Q: What are the four components of <b>Hadoop</b>?</summary><b>Answer</b>: <ol><li><div><a href="https://hadoop.apache.org/">Hadoop</a> -<br> an ecosystem of tools for big data storage and data analysis. Hadoop is<br> an older system than Spark but is still used by many companies.&nbsp;</div><br></li><br><li><div><strong>Hadoop MapReduce</strong> - a system for processing and analyzing large data sets in parallel. </div><br></li><br><li><div><strong>Hadoop YARN</strong> - a resource manager that schedules <br>jobs across a cluster. The manager keeps track of what computer <br>resources are available and then assigns those resources to specific <br>tasks.</div><br></li><br><li><div><strong>Hadoop Distributed File System (HDFS)</strong> - a big data storage system that splits data into chunks and stores the chunks across a cluster of computers.&nbsp;</div><br></li></ol>

<b><i>Remarks</i></b>: The major difference between Spark and Hadoop is how they use memory. Hadoop writes intermediate results to disk whereas Spark tries to keep data in memory whenever possible. This makes Spark faster for many use cases.

</details></p>

<p><details><summary>Q: How does Spark differ from Hadoop?</summary><b>Answer</b>: <ol><li>Spark is generally faster than Hadoop. This is because Hadoop writes 
intermediate results to disk whereas Spark tries to keep intermediate 
results in memory whenever possible.</li><li>The Hadoop ecosystem includes a distributed file storage system called 
HDFS (Hadoop Distributed File System). Spark, on the other hand, does 
not include a file storage system. You can use Spark on top of HDFS but 
you do not have to. Spark can read in data from other sources as well 
such as Amazon S3.<br></li></ol>

</details></p>

<p><details><summary>Q: What is MapReduce?</summary><b>Answer</b>: MapReduce is a programming technique for manipulating large data sets.

<b><i>Remarks</i></b>: &nbsp;"Hadoop MapReduce" is a specific implementation of this programming technique.

</details></p>

<p><details><summary>Q: How does MapReduce work?</summary><b>Answer</b>: <ul><li>The technique works by first dividing up a large dataset and 
distributing the data across a cluster.&nbsp;</li><li>In the <b>map step</b>, each data is 
analyzed and converted into a <b>(key, value) pair</b>.&nbsp;</li><li>Then these key-value 
pairs are <b>shuffled</b> across the cluster so that all keys are on the same 
machine.&nbsp;</li><li>In the <b>reduce step</b>, the values with the same keys are combined 
together.</li></ul>

</details></p>

<p><details><summary>Q: What happens in the shuffle step of MapReduce?</summary><b>Answer</b>: <ul><li>The shuffle step finds all of the data across the clusters that have the
 same key. </li><li>And all of those data points with that key are brought into 
the same network node for further analysis.</li></ul>

</details></p>

<p><details><summary>Q: What are the four modes to set up Spark?</summary><b>Answer</b>: <ol><li>Local</li><li>Spark standalone</li><li>YARN</li><li>Mesos</li></ol>

</details></p>


#### Module 5


##### Introduction To Data Lakes

<p><details><summary>Q: List differences between <b>Data Warehouses</b>&nbsp;and <b>Data Lakes</b></summary><b>Answer</b>: <ol><li><b>Data form</b>: tabular <b>vs.</b> all formats</li><li><b>Data value</b>: high only <b>vs.</b> high- or medium-value, or to be discoverd</li><li><b>Ingestion</b>: ETL <b>vs.</b> ELT</li><li><b>Data model</b>: Star &amp; Snowflake with conformed dimensions or data-marts and OLAP cubes<b> vs. </b>Star &amp; Snowflakes and OLAP are also possible but other ad-hoc represenations are possible</li><li><b>Schema</b>: Known before ingestion (schema-on-write) <b>vs.</b> On-the-fly at the time of analysis (schema-on-read)</li><li><b>Technology</b>: Expensive MPP databases with expensive disks and connectivity <b>vs. </b>Commodity hardware with parallelism as first principle.</li><li><b>Data Quality</b>: High with effort for consistency and clear rules for accessibility <b>vs.</b> mixed, some data remain in raw format, some data is transformed to higher quality</li><li><b>Users</b>: Busines analysts<b> vs.</b> Data scientists, business analysts &amp; ML engineers</li><li><b>Analytics</b>: Reports and business intelligence visualizations <b>vs.</b> Machine Learning, graph analytics and data exploration.</li></ol>

</details></p>

<p><details><summary>Q: What is<b> schema-on-read</b>?</summary><b>Answer</b>: <ul><li>Schema on read refers to an innovative data analysis strategy in new data-handling tools like Hadoop and other more involved database technologies. </li><li>In schema on read, data is applied to a plan or schema as it is pulled out of a stored location, rather than as it goes in.</li></ul>

</details></p>

<p><details><summary>Q: Difference between <b>data warehouses</b> and <b>data lakes</b></summary><b>Answer</b>: <table width="800" height="361" cellspacing="0" cellpadding="1"> 
         <tbody> 
          <tr> 
           <th>Characteristics</th> 
           <th>Data Warehouse</th> 
           <th>Data Lake</th> 
          </tr> 
          <tr> 
           <td><b>Data</b></td> 
           <td>Relational from transactional systems, operational databases, and line of business applications</td> 
           <td>Non-relational and relational from IoT devices, web sites, mobile apps, social media, and corporate applications</td> 
          </tr> 
          <tr> 
           <td><b>Schema</b></td> 
           <td>Designed prior to the DW implementation (schema-on-write)</td> 
           <td>Written at the time of analysis (schema-on-read)</td> 
          </tr> 
          <tr> 
           <td><b>Price/Performance</b></td> 
           <td>Fastest query results using higher cost storage</td> 
           <td>Query results getting faster using low-cost storage</td> 
          </tr> 
          <tr> 
           <td><b>Data Quality<br> </b></td> 
           <td>Highly curated data that serves as the central version of the truth</td> 
           <td>Any data that may or may not be curated (ie. raw data)<br> </td> 
          </tr> 
          <tr> 
           <td><b>Users</b></td> 
           <td>Business analysts</td> 
           <td>Data scientists, Data developers, and Business analysts (using curated data)</td> 
          </tr> 
          <tr> 
           <td><b>Analytics</b></td> 
           <td>Batch reporting, BI and visualizations</td> 
           <td>Machine Learning, Predictive analytics, data discovery and profiling<br> </td> 
          </tr> 
         </tbody> 
        </table>

</details></p>

<p><details><summary>Q: What is a <b>data lake</b>?</summary><b>Answer</b>: <ul><li>A data lake is a centralized repository that allows you to store all 
your structured and unstructured data at any scale. </li><li>You can store your 
data as-is, without having to first structure the data, and run 
different types of analytics—from dashboards and visualizations to big 
data processing, real-time analytics, and machine learning to guide 
better decisions.</li></ul>

<b><i>Example</i></b>: <img src="images/AWS_Analytics_2021_LakeHouse.337c5d294eae24fe954c1d2e93fcda03233dfba4.png">

</details></p>

<p><details><summary>Q: Describe the <b>bottled water vs. data lake analogy</b></summary><b>Answer</b>: <ul><li>A data warehouse is like a producer of water where you are handed bottled water in a particular size and shape</li><li>In contrast, a data lake is a lake where many water streams flow into it and everyone is free to choose the water in the way they want to.</li></ul>

</details></p>

<p><details><summary>Q: What are issues of <b>data lakes</b>?</summary><b>Answer</b>: Data lakes are prone to being a chaotic <b>data garbage dump</b> ("Datensumpf). To prevent this, detailed metadata (e.g. a data catalog) should be put in place.

</details></p>



## Acronyms

RDD: Resilient Distributed Dataset <a href="https://en.wikipedia.org/wiki/Apache_Spark"><img border="0" alt="Wiki link" src="images/Black_W_for_promotion.png" width="30" height="30"></a>

JVM: Java Virtual Machine <a href="https://en.wikipedia.org/wiki/Java_virtual_machine"><img border="0" alt="Wiki link" src="images/Black_W_for_promotion.png" width="30" height="30"></a>

CPU: Central Processing Unit <a href="https://en.wikipedia.org/wiki/Central_processing_unit"><img border="0" alt="Wiki link" src="images/Black_W_for_promotion.png" width="30" height="30"></a>

RAM: Random Access Memory <a href="https://en.wikipedia.org/wiki/Random-access_memory"><img border="0" alt="Wiki link" src="images/Black_W_for_promotion.png" width="30" height="30"></a>

SSD: Solid State Drive <a href="https://en.wikipedia.org/wiki/Solid-state_drive"><img border="0" alt="Wiki link" src="images/Black_W_for_promotion.png" width="30" height="30"></a>

LAN: Local Area Network <a href="https://en.wikipedia.org/wiki/Local_area_network"><img border="0" alt="Wiki link" src="images/Black_W_for_promotion.png" width="30" height="30"></a>

HDFS: Hadoop Distributed File System <a href="https://en.wikipedia.org/wiki/Apache_Hadoop"><img border="0" alt="Wiki link" src="images/Black_W_for_promotion.png" width="30" height="30"></a>

*[RDD]: Resilient Distributed Dataset
*[JVM]: Java Virtual Machine
*[CPU]: Central Processing Unit
*[RAM]: Random Access Memory
*[SSD]: Solid State Drive
*[LAN]: Local Area Network
*[HDFS]: Hadoop Distributed File System
