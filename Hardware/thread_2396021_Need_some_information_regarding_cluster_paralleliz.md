---
title: "Need some information regarding cluster parallelization"
date: 2018-07-10
forum: Hardware
---

### Post by ramkrishnaghosh on 2018-07-10
[FONT=Arial]Hi All, 
I am in fact looking for some basic information regarding hardware specification of clustering/parallelization of different nodes. [/FONT][FONT=Arial]Actually, I want to parallelize different nodes to make a cluster (for example, a cluster with 5 nodes). In that case, is it mandatory that all nodes should have the same configuration (like same no. of cores/clock speed, RAM etc.)? Or, if a heterogeneous cluster is feasible, then will it be possible to make a cluster with 5 nodes having completely different configurations? [/FONT][FONT=Arial]I am looking for your suggestions.[/FONT][FONT=Arial]

Thanks
Ram[/FONT]

---

### Post by TheFu on 2018-07-10
Welcome to the forums.

So, to get any help, the specific clustering software you  plan on using, if it isn't 100% custom, needs to be clarified.  I think there are over 20 reasonable tools.  We cannot guess.

Also, there are at least 5 different types of "clusters", please be specific.

---

### Post by 1clue on 2018-07-10
Clustering is a separate field of study. I have done some reading but am not knowledgeable the way somebody who does this would be.

Whether a cluster benefits your problem domain or not, and how the cluster would be configured, depends on the problem to be solved. Most clusters are made to solve a single type of problem.

Some clusters have a specific order of processing, like an assembly line. Node A gets data, performs calculations and then sends the output to node B. Node B gets the data, performs calculations and sends the output to node C. And so on.

Some clusters are heterogeneous, which means that there is a pile of data points and each node in the cluster grabs one, performs calculations and then pushes the output before going onto the next one.

There can be a huge number of variations. Any way you can imagine connecting multiple machines to solve a single problem, a cluster could be built that way.

One thing that most people leave out is that there must be some sort  of control infrastructure which makes the group of computers into a  cluster. It could theoretically be ONLY a bit of software on one of the  nodes, but probably there is hardware dedicated to reading data off the  storage device, setting up the queue and collecting data. The clustering  software is a significant overhead, meaning not a tiny fraction of the  total capability of the cluster.

Clusters are very sensitive to many variables. Buying the wrong network card can trash the performance of the cluster. Many clusters have millions of cores and some have millions of nodes. If you bought the wrong NIC for USD $100 each on, say, a million node cluster, you just wasted $100 million. I understand you're not talking about a large cluster, but I'm simply trying to provide an example of how things can go wrong. Likewise the network switches, the physical layout of the network, the RAM used, the disks used and the software all make a massive difference to the performance.

One thing that many people don't understand is that in order for a cluster to be cost effective, it must use hardware which is produced in large quantities and which performs extremely well per unit cost. If you visit top500.org you can spend time with the sublist generator and  find out what most of those clusters use. Last I checked, roughly 80% of the systems used multi-socket boards with Intel E5 chips, with 8-16 cores per socket. Surprisingly to me, very few systems had a large amount of RAM per node.

There is a ton of reading material on this. I would recommend strongly that you avoid some random person's blog and look to the credentials of the author. While there is a lot of credible real-world expertise writing information about this, there is a ton of highly enthusiastic but mostly ignorant postings from people who "made a cluster" out of junk hardware or raspberry pi's or some such. In many cases they started writing their article/blog post before they even bought the equipment, and they simply assume that the cluster will perform better than a bigger computer would have performed.

---

### Post by ramkrishnaghosh on 2018-07-12
Hi, 
Thank you for your reply. It's indeed helped me a lot to understand about clustering. I am in fact planning to build a cluster of five nodes with Ubuntu OS. Do I need any additional software for the clustering? 

You have also mentioned that most of the system uses multi-socket board with Intel E5 chip,  so is it mandatory that the processors in all nodes should have the same type of processors? For an example, if I have one node with Intel Xeon E5 processors (12x2 cores), then can I combine this with another node with Xeon Gold processor(12x2 cores)? Or all the nodes should have the same series of processors?

Regards, 
Ramkrishna

---

### Post by TheFu on 2018-07-12
"cluster" is a very generic term, seems you are misunderstanding that.  There isn't 1 clustering solution. There are many.

Nothing is mandatory (same CPU) unless the clustering software you are using makes it mandatory.  There are 20 different clustering tools and you haven't said which you are planning to use.  Management for huge clusters is easier when the CPUs all support the same instructions.  There are slight differences in the supported instructions between different chip models. This makes optimizing the code per-CPU harder and can have minor or huge performance impacts.

[https://www.howtoforge.com/tutorial/ubuntu-docker-swarm-cluster/](https://www.howtoforge.com/tutorial/ubuntu-docker-swarm-cluster/)

There are HA clusters like DB failover clusters.
There are front-end clusters to share the load.
And every sort of compute-only cluster is a snowflake - that means they are all different based on the problem being solved and custom code is required to use them.

---

### Post by 1clue on 2018-07-12
"Additional software for clustering". You mean besides what's in the repository already? Probably not but you haven't said anything about your project, and I probably don't have expertise to guide you to any particular application anyway since I've never actually built a cluster.

There's no requirement of all the systems having the same processor. If you are creating a homogeneous pool of nodes, then usually you would try for a bunch of the same thing. That's an advantage for several reasons:
[LIST=1]
[*]Prediction of completion times is easier
[*]Buying hardware is easier
[*]Buying spare parts is easier
[*]Maintenance is easier
[*]...
[/LIST]

All that said, I understand that often the control nodes have different requirements and therefore might be different hardware, Likewise if you're using a pipeline style architecture each node might be tailored for that particular task.

You're talking about 5 nodes. If you just want to prove that you can make a cluster, then a raspberry pi will work, there's tons of projects online showing how it's done. My comments about systems on top500.org are to give you an idea what is considered to be "node-worthy" hardware for organizations that use clusters to do real work. An E5 system can set you back enough to pay for a house in some places in the world, but that's what is considered the best "bang for the buck" for hardware.


I'm going to make a guess here. I speculate that you're simply curious about clusters and want to try it as an intellectual exercise.

The reason I'm saying this is because the normal procedure is to have a problem which needs solving and then in researching the possible solutions you determine that a single system can't reasonably solve that problem. You then break the problem down into its essential parts and eventually your cluster's structure is evident.

As I said before, clusters are sensitive to many things, and most clusters are built to solve one type of problem only. That's because there's a lot of tuning to make the cluster efficient and effective. The problem domain defines not just the arrangement of nodes, but the type of hardware which is best to use as a node. In some cases a graphics card or nintendo box seems to be appropriate. In others an E5 system. You won't know until you have your problem domain broken down adequately.

So, because you have come here and asked very basic questions about clusters rather than describing your problem which needs solving, I'm going to say you're just curious. That's no problem, it's how I learned. I'm very interested in how clusters work, but my problem is that I'm not interested in many of the problems which benefit from clusters. I'm unwilling to invest in hardware which will be used just to make an effective cluster, that I really have no other use for, and that has no problem to solve.

My solution was to spend a few weeks with Google and read everything I could find about how clusters work and how problems are solved with them.

---

### Post by ramkrishnaghosh on 2018-07-12
Hi All, 
Thank you for your kind reply. I am basically working on solving mathematical equations in several serial nodes with multiple cores (of course, with the different processor as well). However, it usually takes several days to execute the jobs in serial running. Therefore, I am trying to combine those to make a cluster using torque in Ubuntu server OS. I am very much new in understanding/implementing clustering. Therefore, I have tried to google to understand about the hardware/software/package requirement in the clustering of nodes. However, it is quite confusing because there are a lot of different responses and so I thought, it's better to clarify myself from an expert regarding hardware/software/package requirements. It will be very much helpful if you guide me to configure my system. The link on "swarm-clustering" is indeed very helpful. 

Thanks
Ram

---

### Post by TheFu on 2018-07-12
You have little use for a docker cluster.  Interesting as that might be, it isn't useful for your work.

First, you should create multithreaded solutions to the problem and tune those.  For example: 
[https://antlarr.io/2018/07/optimizing-a-python-application-with-c-code/](https://antlarr.io/2018/07/optimizing-a-python-application-with-c-code/)
Until you can chunk up the work to be performed into unrelated tasks, compute clustering won't work for you. In business, it is often more cost effective to just buy a bigger, faster, server than to deal with clustering.  Some problems can't be chunked in a way that matters.

I was  an expert at DB clustering for HA about 10 yrs ago, but not on Linux.  I still do load-balance front-end clustering on Linux today, but that isn't useful for what you've described. I also have a batch process that shifts work from system to system overnight to finish processing before the morning.  As each input is handled, the output gets fed into another system for more processing.  This is around video editing and transcoding. 3 different systems are involved. Each video is a different chunk separate from the others.  I move the output from each task onto the next step through scripting.  Basically, it is a batch pipeline. Some might call it a "cluster", but I just use a batch queueing tool - task spooler - on each of the systems to keep them busy but not overflowing with work.

But none of this is helpful to you. Sorry.

---

### Post by 1clue on 2018-07-12
> **ramkrishnaghosh said:**
> Hi All, 
Thank you for your kind reply. I am basically working on solving mathematical equations in several serial nodes with multiple cores (of course, with the different processor as well). However, it usually takes several days to execute the jobs in serial running. Therefore, I am trying to combine those to make a cluster using torque in Ubuntu server OS. I am very much new in understanding/implementing clustering. Therefore, I have tried to google to understand about the hardware/software/package requirement in the clustering of nodes. However, it is quite confusing because there are a lot of different responses and so I thought, it's better to clarify myself from an expert regarding hardware/software/package requirements. It will be very much helpful if you guide me to configure my system. The link on "swarm-clustering" is indeed very helpful. 

Thanks
Ram

Do you have all cores utilized when running serially? If your program does not explicitly use multiple threads then you are running with just one core.

Your problem must be in some way broken down into independent parts. Do you have many unrelated data points which must be processed in the same way? Or specific steps where step 1's output can be fed into step 2, and each step requires significant calculation?

Things to keep in mind:
[LIST=1]
[*]Parallelism has an overhead. It takes CPU cycles to set up parallelism even on a single CPU. Tasks must be scheduled and executed in a sensible fashion.
[*]Parallelism within a CPU (core to core) is fastest. Communication between cores is very fast and requires the least overhead.
[*]Parallelism between sockets is slower but still fast.
[*]Parallelism between nodes is slowest. Here the transmission time between nodes is significant.
[/LIST]

Clusters are only good for tasks where the calculation time of the task is significantly large compared to transmission/communication time.

It sounds like you have a large problem, but the question is how can it be broken up? The easiest way to deal with is if you have many discrete data sets which can be independently processed. Otherwise (based on your comments) a serial set of calculations could possibly be fed from node to node, but the length of calculation needs to be large compared to communication time as I said.

---

