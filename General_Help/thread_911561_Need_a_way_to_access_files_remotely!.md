---
title: "Need a way to access files remotely!"
date: 2008-09-05
forum: General Help
---

### Post by es926 on 2008-09-05
Hello,

Here's my situation. I have a large data set on a local server that I need to analyze on a far off server (where I don't have root access). I don't have enough scratch space on the remote server to store the data set (so scp/sftp isn't practical). I'm currently running an ssh server and an nfs server on the local server. I have ssh access to the remote server but only after going through gateway servers.

Everything would be great if I could somehow mount a directory on my local server (through sshfs, nfs, etc...) but I don't think that this is possible without root access. Does anybody have any ideas of how I could possibly access my local files remotely? Is the bottom line that I just can't do it without root access?

PS I'm aware that I could break up the local files, transfer a few, analyze them, delete them, transfer some more, etc but this would require a major restructuring of my analysis code, so an alternative would be ideal.

---

### Post by afbase on 2008-09-05
> **es926 said:**
> Hello,

Here's my situation. I have a large data set on a local server that I need to analyze on a far off server (where I don't have root access). I don't have enough scratch space on the remote server to store the data set (so scp/sftp isn't practical). I'm currently running an ssh server and an nfs server on the local server. I have ssh access to the remote server but only after going through gateway servers.

Everything would be great if I could somehow mount a directory on my local server (through sshfs, nfs, etc...) but I don't think that this is possible without root access. Does anybody have any ideas of how I could possibly access my local files remotely? Is the bottom line that I just can't do it without root access?

PS I'm aware that I could break up the local files, transfer a few, analyze them, delete them, transfer some more, etc but this would require a major restructuring of my analysis code, so an alternative would be ideal.
Have you investigated [Hadoop MapReduce]("http://wiki.apache.org/hadoop/HadoopMapReduce")?

---

### Post by afbase on 2008-09-05
> **es926 said:**
> Hello,

Here's my situation. I have a large data set on a local server that I need to analyze on a far off server (where I don't have root access). I don't have enough scratch space on the remote server to store the data set (so scp/sftp isn't practical). I'm currently running an ssh server and an nfs server on the local server. I have ssh access to the remote server but only after going through gateway servers.

Everything would be great if I could somehow mount a directory on my local server (through sshfs, nfs, etc...) but I don't think that this is possible without root access. Does anybody have any ideas of how I could possibly access my local files remotely? Is the bottom line that I just can't do it without root access?

PS I'm aware that I could break up the local files, transfer a few, analyze them, delete them, transfer some more, etc but this would require a major restructuring of my analysis code, so an alternative would be ideal.
Have you investigated [Hadoop MapReduce]("http://wiki.apache.org/hadoop/HadoopMapReduce")?

well on second thought.  Can you SSH to your local server from the remote server?

---

### Post by panayk on 2008-09-05
> **es926 said:**
> Everything would be great if I could somehow mount a directory on my local server (through sshfs, nfs, etc...) but I don't think that this is possible without root access.

Actually, as far as I remember, sshfs does not require root access neither on the remote machine, nor the local machine (beyond adding the user to the fuse group on the latter).

[http://www.debianadmin.com/mount-a-remote-file-system-through-ssh-using-sshfs.html](http://www.debianadmin.com/mount-a-remote-file-system-through-ssh-using-sshfs.html)

---

