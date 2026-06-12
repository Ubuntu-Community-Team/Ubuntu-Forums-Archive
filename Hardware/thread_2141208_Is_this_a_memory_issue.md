---
title: "Is this a memory issue?"
date: 2013-05-02
forum: Hardware
---

### Post by billcauley on 2013-05-02
The memory usage starts at 22% but slowly builds, and reaches 70% after 10 hours of uptime.  If left alone, the swap file will start being used, and eventually programs slow to being unusable.  **Logging out/in recovers the memory!**  Shouldn't the memory be releasing after use?  Is this a concern?

---

### Post by Cheesemill on 2013-05-02
Which process has the memory leak? You can use top to find out if you're not sure.

---

### Post by billcauley on 2013-05-02
I've looked at the list, and don't see that anything is "leaking"; though I might be looking at the wrong things.

---

### Post by grahammechanical on 2013-05-02
First, what version of Ubuntu? Second, how much memory. 70% of 1GB is not the same as 70% of 2GB.

I have found that Ubuntu versions prior to 13.04 always used about 70% of 1GB of RAM on my machine. The system does not release memory quickly. It likes to keep memory reserved once it has been used in case that memory space is need again.

On 13.04 memory usage is down by 15 - 20% until I start loading applications then it builds up a bit.

Regards.

---

### Post by billcauley on 2013-05-02
I've got 2GB, but the issue is not how much, but that it's not releasing and continues to build until things slow to the point of becoming unusable. Using Ubuntu 13.04 classic.

---

### Post by dabl on 2013-05-02
As Cheesemill says, if you run top, after the system has been up for some hours, it should be apparent which process is hogging the memory.  You won't actually observe it leaking, probably, but one process will be using way more memory than the others.

---

### Post by billcauley on 2013-05-02
Yes, TOP does show the relative memory usage, but I'm thinking that it shouldn't continue to build.  Shouldn't memory be released without my having to log out and then in, or rebooting?

---

### Post by dabl on 2013-05-02
You are completely correct -- it is undoubtedly a bug in some bit of software, possibly the OS, possibly something else that is running.  But it can't get fixed until it gets reported, and it can't get reported until someone can define the problem with reasonable precision.

---

