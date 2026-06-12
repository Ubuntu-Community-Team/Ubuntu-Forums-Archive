---
title: "Monitor GPU Usage"
date: 2008-05-18
forum: Hardware
---

### Post by ipburbank on 2008-05-18
Hi all! On my mac I have the ability to see my GPU usage right along with my CPU, RAM etc. Is there a way to do this on Ubuntu as well? I am using an nvidia 9600.

---

### Post by neo_adi on 2008-05-18
[QUOTE="ipburbank"]Hi all! On my mac I have the ability to see my GPU usage right along with my CPU, RAM etc. Is there a way to do this on Ubuntu as well? I am using an nvidia 9600.[/QUOTE]

all that you have to do is to cat meminfo and cpuinfo in the proc directory

for Memory usage : 

> cat /proc/meminfo 

for cpu usage: 
> cat /proc/cpuinfo  

this will do the job for sure ;)

---

### Post by ipburbank on 2008-05-18
Great thanks. That works now, but I still can't see the GPU usage....

---

### Post by ipburbank on 2008-08-29
hey guys, i'm looking into more parts for my computer, and I would like to be able to monitor this to help decide what i should buy, so if there is someone who can help... please?

---

### Post by ipburbank on 2008-09-28
I have another thread, it also is about what to upgrade, and it would be great if there was a way to measure the gpu, because that would make the other thread go more smoothly.

---

