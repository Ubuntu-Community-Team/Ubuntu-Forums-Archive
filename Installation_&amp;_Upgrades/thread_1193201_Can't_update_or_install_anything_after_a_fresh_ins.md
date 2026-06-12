---
title: "Can't update or install anything after a fresh install"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by tzg6sa on 2009-06-21
Hi!

I have just installed the new Ubuntu 9.04. My problem started in 8.10. When I wanted to upgrade (after checking the software sources step) it said that some deb packages can not be fetched. The error code was "Sub-process bzip2 returned an error code (2)". After that I decided to format the partition and install 9.04 instead of upgrading. The problem remained the same. :( What I find very strange.

I tried to used different servers.
I have tried
```

sudo apt-get clean
sudo apt-get update

```

During the update I get the following error:
In the middle of the output I get the following (and a similar one which I do not copied here):
```

Get:3 http://ftp.freepark.org jaunty/universe Packages [4757kB]
27% [1 Packages bzip2 5423104] [3 Packages 844/4757kB 0%]  
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://ftp.freepark.org jaunty/main Packages         
  Sub-process bzip2 returned an error code (2)

```
And at the end of the output:
```

Fetched 6564kB in 14s (452kB/s)                                                
W: Failed to fetch http://ftp.freepark.org/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://ftp.freepark.org/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I have tried aptitude instead of apt without success.
I have tried the suggestion in [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=4952791&postcount=10](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=4952791&postcount=10) but it did not help.

Please help me!

---

### Post by Amilo1718 on 2009-06-21
& when you use the gui? update manager?

---

### Post by drs305 on 2009-06-21
Before researching the possibility of problems with your system it is more likely that the files on the server have problems.

Try using another server. Either Software Sources, or Synaptic: Settings, Repositories, "download from" and select a different server. Then press the "Reload" button at the top of the menu.

---

### Post by tzg6sa on 2009-06-21
Thanks for the quick replies!

The problem exist with GUI too. (First I used the GUI. I switched to command line to get more debugging info)

I have tried many server. The main one, servers form UK, USA, Germany, Austria, Spain and both from my country. The problem exist in all cases. The only difference is the number of errors. Some cases i have got even 6 error messages. (failed to fetch [http://thenameofthepackage/Packages.bz2](http://thenameofthepackage/Packages.bz2) Sub-process bzip2 returned an error code (2))

---

### Post by tzg6sa on 2009-06-22
Any idea?

---

### Post by drs305 on 2009-06-23
> **tzg6sa said:**
> Any idea?

Since you have tried different servers the problem should not be in your lists, but we can try to clear them out and get a completely new list just to rule out the possibility of a bad list:
```

sudo mv /var/lib/apt/lists /var/lib/apt/lists.old # Rename current *lists* folder
sudo mkdir /var/lib/apt/lists /var/lib/apt/lists/partial # Create new empty *list* and *list/partial* folders
sudo touch /var/lib/apt/lists/lock  # Recreate the *lock* file
sudo apt-get update

```

If this doesn't fix the problem, let us know. You might also post your /etc/apt/sources.list file since that is the base we are working from.

---

### Post by tzg6sa on 2009-06-24
Hi! Thank you for your answer. I found it especially good the way how you explained what the commands do.
The update still does not work :(

Here are the outputs of the commands:
```

tibenszky@vacak:~$ sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
[sudo] password for tibenszky: 
tibenszky@vacak:~$ sudo mkdir /var/lib/apt/lists /var/lib/apt/lists/partial
tibenszky@vacak:~$ sudo touch /var/lib/apt/lists/lock


tibenszky@vacak:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com jaunty Release.gpg [189B]
Ign http://archive.ubuntu.com jaunty/main Translation-en_US
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US
Get:2 http://archive.ubuntu.com jaunty-updates Release.gpg [189B]
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
Get:3 http://archive.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_US
Get:4 http://archive.ubuntu.com jaunty Release [74.6kB]
Get:5 http://archive.ubuntu.com jaunty-updates Release [49.6kB]
Get:6 http://archive.ubuntu.com jaunty-security Release [49.6kB]
Get:7 http://archive.ubuntu.com jaunty/main Packages [1253kB]
Get:8 http://archive.ubuntu.com jaunty/restricted Packages [8848B]
Get:9 http://archive.ubuntu.com jaunty/multiverse Packages [197kB]
Get:10 http://archive.ubuntu.com jaunty/universe Packages [4757kB]
33% [7 Packages bzip2 7053312] [10 Packages 513671/4757kB 10%]
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com jaunty/main Packages            
  Sub-process bzip2 returned an error code (2)
33% [9 Packages bzip2 0] [10 Packages 538287/4757kB 11%]      
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com jaunty/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Get:11 http://archive.ubuntu.com jaunty/main Sources [555kB]                   
Get:12 http://archive.ubuntu.com jaunty/restricted Sources [3156B]             
Get:13 http://archive.ubuntu.com jaunty/universe Sources [2375kB]              
77% [10 Packages bzip2 6918144] [13 Sources 260580/2375kB 10%]       583kB/s 3s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com jaunty/universe Packages                         
  Sub-process bzip2 returned an error code (2)
Get:14 http://archive.ubuntu.com jaunty-updates/main Packages [89.2kB]         
Get:15 http://archive.ubuntu.com jaunty-updates/restricted Packages [2092B]    
Get:16 http://archive.ubuntu.com jaunty-updates/multiverse Packages [675B]     
Get:17 http://archive.ubuntu.com jaunty-updates/universe Packages [24.3kB]     
Get:18 http://archive.ubuntu.com jaunty-updates/main Sources [29.1kB]          
Get:19 http://archive.ubuntu.com jaunty-updates/restricted Sources [611B]      
Get:20 http://archive.ubuntu.com jaunty-updates/universe Sources [7154B]       
Get:21 http://archive.ubuntu.com jaunty-security/main Packages [36.4kB]        
Get:22 http://archive.ubuntu.com jaunty-security/restricted Packages [14B]     
Get:23 http://archive.ubuntu.com jaunty-security/multiverse Packages [14B]     
Get:24 http://archive.ubuntu.com jaunty-security/universe Packages [10.3kB]    
Get:25 http://archive.ubuntu.com jaunty-security/main Sources [10.8kB]         
Get:26 http://archive.ubuntu.com jaunty-security/restricted Sources [14B]      
Get:27 http://archive.ubuntu.com jaunty-security/universe Sources [2282B]      
99% [13 Sources bzip2 3596288]                                       513kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com jaunty/universe Sources                          
  Sub-process bzip2 returned an error code (2)
99% [14 Packages bzip2 0]                                            513kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://archive.ubuntu.com jaunty-updates/main Packages                     
  Sub-process bzip2 returned an error code (2)
Fetched 9535kB in 19s (482kB/s)                                                
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2  Sub-process bzip2 returned an error code (2)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

And here is my sources.list after the commands above. I have deleted the commands generated automatically. 
```

tibenszky@vacak:~$ cat /etc/apt/sources.list
jaunty main restricted
jaunty main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
restricted universe multiverse
restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe

```

I hope you will find something. Thank you in advance.

---

### Post by drs305 on 2009-06-24
> **tzg6sa said:**
> 
And here is my sources.list after the commands above. I have deleted the commands generated automatically. 
```

tibenszky@vacak:~$ cat /etc/apt/sources.list
[B][COLOR="Red"]jaunty main restricted
jaunty main restricted[/COLOR][/B]
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
[B]restricted universe multiverse
[COLOR="Red"]restricted universe multiverse[/COLOR][/B]
deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe

```

I hope you will find something. Thank you in advance.

It is hard to tell if your sources.list contains line breaks or if the output was broken up during the cut & paste. Every line in your sources.list should start with "**deb**". I have highlighted the sections of your sources.list that do not. Take a look at the original file and check those entries. Definitely remove the ones in red. The black bold line should probably be put at the end of the preceeding line.

The end result should look something like this. I have copied a valid sources.list file. For simplicity, you can replace your corrupted sources.list with this one:

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse


To replace it or edit it:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bad # back up old file
gksudo gedit /etc/apt/sources.list  # Open sources.list for editing

```
Save the file, then run your update command again.
Once it is working you can change the server to something else if you prefer (Synaptic, Settings, Repositories, Download from...")

---

### Post by tzg6sa on 2009-06-24
Hi!

Every line started with deb, just the lines were wrapped. I have used the sources.list file you have given, but the problem is the same. I have got error messages at jaunty-security/universe Sources and jaunty/universe Sources ("Sub-process bzip2 returned an error code (2)").

---

### Post by drs305 on 2009-06-24
> **tzg6sa said:**
> Hi!

Every line started with deb, just the lines were wrapped. I have used the sources.list file you have given, but the problem is the same. I have got error messages at jaunty-security/universe Sources and jaunty/universe Sources ("Sub-process bzip2 returned an error code (2)").

Do you use any of the src repositories (do you compile your own apps)? If not, you could deselect the "source" repositories in Synaptic: Settings, Repositories, Ubuntu Software: Source Code.

I don't think that is your underlying problem but since they are the ones giving you errors if you don't need them, disable them.

---

### Post by onomou on 2009-06-28
Interesting... I have had the same sort of problem as tzg6sa and tried the suggestions given. Nothing worked until I disabled the source code in Software Sources. Before, it had strangely not had a check mark but only the orange box filled in. I still can't get it to put a check mark there, but disabling it and changing my mirror to PDX made it so I could update Aptitude without any errors and upgrade my packages.

tzg6sa - any luck for you?

Many thanks to drs305, I should have thought of disabling different sources; it worked for me!

---

### Post by tzg6sa on 2009-06-30
The problem was caused by my router. Some packages were received corrupt. I have noticed, that all zip files what I have downloaded was corrupted, and many (Windows) installation files did the same. Altough I could surf on the web at the same time. It suggested me that it is not a software issue. I have bypassed my router and this way I have no problem at all.

---

