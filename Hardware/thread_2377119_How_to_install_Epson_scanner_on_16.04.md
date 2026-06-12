---
title: "How to install Epson scanner on 16.04?"
date: 2017-11-09
forum: Hardware
---

### Post by daniell59 on 2017-11-09
I recently installed Synaptic Package Manager. In spite of my efforts, I have not been able to understand how to use it. I would appreciate it if someone could give me some hints on how to begin. In particular, I would like to start with [http://support.epson.net/linux/en/iscan.php?model=gt-f720&version=1.0.1](http://support.epson.net/linux/en/iscan.php?model=gt-f720&version=1.0.1)

Ubuntu 16.04 64

Thanks in advance

---

### Post by ajgreeny on 2017-11-09
Synaptic will not help you with that installation; synaptic is for downloading and installing packages from the normal repositories, not for manual installation of packages downloaded as you have done.

From the link you showed us you can download a tar.gz archive file for Ubuntu of the correct architecture, which you will then need to double click to see what it contains and to extract the folder.

That folder has a **Readme.rst** file and an **install.sh** file which is a shell script to carry out the actual installation.
The Readme.rst file is a text file and tells you what to do, so open that, follow the instructions and if still stuck come back again with as much detail of the problems you're facing and we'll try to help you.

---

### Post by daniell59 on 2017-11-09
```
daniel@daniel-N68SA-M2S:~/Desktop$ cd Desktop
bash: cd: Desktop: No such file or directory
daniel@daniel-N68SA-M2S:~/Desktop$ ls
audio-recorder_2.0.2~artful_amd64.deb
google-chrome-stable_current_amd64.deb
hplip-3.17.10
hplip-3.17.10.run
iscan-gt-f720-bundle-1.0.1.x64.deb
iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz
daniel@daniel-N68SA-M2S:~/Desktop$ install.sh
install.sh: command not found
daniel@daniel-N68SA-M2S:~/Desktop$
```

I must be doing something wrong.

---

### Post by deadflowr on 2017-11-09
> **daniell59 said:**
> daniel@daniel-N68SA-M2S:~/Desktop$ cd Desktop
bash: cd: Desktop: No such file or directory
daniel@daniel-N68SA-M2S:~/Desktop$ ls
audio-recorder_2.0.2~artful_amd64.deb
google-chrome-stable_current_amd64.deb
hplip-3.17.10
hplip-3.17.10.run
iscan-gt-f720-bundle-1.0.1.x64.deb
iscan-gt-f720-bundle-1.0.1.x64.deb.tar.gz
daniel@daniel-N68SA-M2S:~/Desktop$ install.sh
install.sh: command not found
daniel@daniel-N68SA-M2S:~/Desktop$ 

I must be doing something wrong.

Yes.
to install the iscan deb file run
```
sudo apt install ~/Desktop/iscan-gt-f720-bundle-1.0.1.x64.deb
```
or if in the ~/Desktop directory simply run
```
sudo dpkg -i iscan-gt-f720-bundle-1.0.1.x64.deb
```

The difference between the *apt install *and *dpkg -i* command is that apt can deal with any dependency issues, where as dpkg does not.
So dpkg can error out if any dpends are missing or not up-to-date or has other problems with them.
Apt install does require that you use the full path to the deb file where dpkg can run full path or just the name if the file is in the current directory.

Hope it helps

---

### Post by daniell59 on 2017-11-09
```
daniel@daniel-N68SA-M2S:~$ cd Desktop
daniel@daniel-N68SA-M2S:~/Desktop$ sudo apt install ~/Desktop/iscan-gt-f720-bundle-1.0.1.x64.deb
[sudo] password for daniel: 
Reading package lists... Error!
E: Sub-process Popen returned an error code (2)
E: Encountered a section with no Package: header
E: Problem with MergeList /home/daniel/Desktop/iscan-gt-f720-bundle-1.0.1.x64.deb
E: The package lists or status file could not be parsed or opened.
daniel@daniel-N68SA-M2S:~/Desktop$ sudo dpkg -i iscan-gt-f720-bundle-1.0.1.x64.deb
dpkg-split: error: error reading iscan-gt-f720-bundle-1.0.1.x64.deb: Is a directory
dpkg:../../src/unpack.c:123:deb_reassemble: internal error: unexpected exit status 2 from dpkg-split
Aborted (core dumped)
daniel@daniel-N68SA-M2S:~/Desktop$
```

---

### Post by deadflowr on 2017-11-09
Ah.
So upon downloading the package myself, I see it's not a deb binary package at all, but rather just a zip like folder
(the 3 sub folders core data and plugins do themselves contain actual deb binary packages, though, fwiw)

So what you need to do is cd into the deb folder like
```
cd Desktop
cd iscan-gt-f720-bundle-1.0.1.x64.deb
sudo ./install.sh
```

the install script then runs an update and downloads any packages not already on the system that it needs and then installs the deb packages from the core data and plugins directories.

Hope that makes some sense.

Note there is a nice little README file in the same folder as the install.sh script.

---

### Post by daniell59 on 2017-11-09
It seems like the program installed. When I tried to use the scanner I got the following.

HPLIP cannot detect devices in your network. This may be due to existing firewall settings blocking the required ports like (5353/udp). When you are in a trusted network environment, you may open the ports for network services like mdns and slp in the firewall. For detailed steps follow the link.

 [http://hplipopensource.com/node/375](http://hplipopensource.com/node/375)

---

### Post by ajgreeny on 2017-11-09
Why does hplip have anything to do with your Epson scanner? The hplip package is for HP devices, not Epson.

---

### Post by daniell59 on 2017-11-09
Thanks for you input. I was thinking the same. I guess that it was in the desktop directory, and somehow got involved. Any additional input would be appreciated.

---

### Post by ajgreeny on 2017-11-10
Do you have or have you had an HP scanner connected to your system that has not been removed?

---

### Post by daniell59 on 2017-11-10
> **ajgreeny said:**
> Do you have or have you had an HP scanner connected to your system that has not been removed?

It was an HP printer.

---

### Post by slickymaster on 2017-11-10
*Thread moved to **Hardware**.*

@daniell59:
Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by daniell59 on 2017-11-10
So where do I go from here?

---

### Post by ajgreeny on 2017-11-10
I am not sure where you go from here and I am still confused and lost about what you're doing and why !

You say in post #7 > It seems like the program installed. When I tried to use the scanner I got the following. and I assume that is the Epson software as explained by deadflowr in post #6 that you think was installed?
Do you actually have an Epson scanner or are you using only an HP AIO printer/scanner?

If you do have an Epson scanner, what model is it, and is it now found by either simple-scan or xsane if you try to scan something using it?

---

### Post by daniell59 on 2017-11-10
I have the Epson Perfection V30 scanner.

---

### Post by ajgreeny on 2017-11-10
And is it found when you start **simple scan** or **xsane**?

---

### Post by daniell59 on 2017-11-10
I turned on the scanner. Not only was it detected, but it now scans perfectly. Before I mark this as solved, could somebody please explain to me what happened. 
Again, let me thank the many who helped make this possible. I wish that I could blame my disorderly mind on old age, but I have always been this way.

---

### Post by ajgreeny on 2017-11-10
It is difficult to know what happened other than that you did, as you thought, install the Epson software meaning the scanner is now found by your scanning program.

I am not sure what application you were using previously to try to scan, but when you got that message "HPLIP cannot detect devices in your network." it makes me wonder if you were using the hplip-gui which has a scan icon in the left-hand pane, which could not find any devices as you had no HP device for it to detect.

Either way it is now working so please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

