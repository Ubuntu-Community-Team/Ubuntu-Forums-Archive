---
title: "java installation problem in ubuntu"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by popprem on 2009-04-16
Hi,

I tried to install java6 in ubuntu 8.04 using jdk-6u3-linux-i586.bin. (downloaded from sun website)

when i try to run the file :

sh jdk-6u3-linux-i586.bin

i got error saying ./install.sfx.nnnn: not found.

The file didnt extracted. Then i changed the file name from .bin to .zip & extracted it manually.

After that when i try to run i got error saying :

jdk1.6.0_13/bin/unpack200: not found
jre/lib/rt.jar
Installation failed.

what can i do to get this fixed & install java properly?
I need help in this matter.
Thanks in advance.

---

### Post by tommcd on 2009-04-16
There is a java package in the Ubuntu repositories. First, make sure you have the universe and multiverse repos enabled:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
Then open synaptic package manager:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
and search for **sun-java6-jre**. Right click on that and select "mark for installation", then "apply" and it will be installed.

Or open a terminal (applications > accessories > terminal) and run:
```

sudo apt-get update
sudo apt-get install sun-java6-jre 

```

And welcome to the Ubuntu forums!

---

### Post by popprem on 2009-04-16
Thanks for the reply tommcd.

 I'm trying to install offline since i do not have internet access at home.

 So, i'm manually running jdk-6u13-linux-i586.bin file as super user. and then i get these errors.

 Can you please help me with this problem?

 Thanks.

---

### Post by Apoorvbarwa on 2009-04-16
open terminal 
go to the directory where file is...
then type 
chmod a+x jdk-6u3-linux-i586.bin
if this dont work try 
user@user-destop:~$ su
password: type password
and then
chmod a+x jdk-6u3-linux-i586.bin
tell me if it works

---

### Post by popprem on 2009-04-16
I already did that Apoorvbarwa.

 It threw an error that ./install.sfx not found, and failed to extract.
 And then i manually extracted in and run again.
 Then it ended up with:

jdk1.6.0_13/bin/unpack200: not found
jre/lib/rt.jar
Installation failed.

 Wt can be the problem?

 Thanks a lot for your reply.

---

### Post by kpkeerthi on 2009-04-16
The jdk-6u3-linux-i586.bin file you downloaded is probably corrupt. Did you verify it MD5 sum?

```

md5sum <file-name>

```

---

### Post by john236 on 2009-06-08
popprem, I'm having the same problem after installing 9.04.  Did you find out what was causing it?  Installing java this way worked in 8.10

---

