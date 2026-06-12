---
title: "UDF-fs data of optical drive media by kernel"
date: 2021-12-22
forum: Hardware
---

### Post by jlivin252 on 2021-12-22
Hi Folks

First of all, Happy Christmas!

I was wondering if anyone can help me understand and explain a query i have around optical disc data and how this is handled by ubuntu.

*Expected behaviour*
When i insert an optical disk into my optical drive I expect that ubuntu will handle the disk, extracting information and potentially auto-mounting the media to a location, I can observe this by watching the syslog, eg.

```
[COLOR=#000000][FONT=Menlo]Dec 22 19:49:58 mysystem systemd[1]: Started Clean the /media/testuser/LOGICAL_VOLUME_ID mount point.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Dec 22 19:49:58 mysystem udisksd[1118]: Mounted /dev/sr1 at /media/testuser/LOGICAL_VOLUME_ID on behalf of uid 1000[/FONT][/COLOR]
```[COLOR=#000000][FONT=Menlo]

I can then do things like:
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Menlo]**testuser@mysystem**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]:[/FONT][/COLOR][COLOR=#5620F4][FONT=Menlo]**~**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]$ [/FONT][/COLOR][COLOR=#000000][FONT=Menlo]blkid -o value -s LABEL /dev/sr1[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Menlo]
to get the name/label of the drive...
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Menlo]LOGICAL_VOLUME_ID[/FONT][/COLOR]
```

...all fine.  Sometimes however the name/label of the media in the drive isn't that helpful, as exampled above.

*Observation*
I was watching the log recently and i noticed that immediately before the mounting process above the log records another action and this gives further information about the media being inserted.

```
[COLOR=#000000][FONT=Menlo]Dec 22 19:49:58 mysystem kernel: [39855.352631] UDF-fs: INFO Mounting volume '57760311_A_USEFUL_NAME', timestamp 2006/11/18 04:09 (1000)[/FONT][/COLOR]
```

In this line i can see data I know belongs to the media i inserted and the line shows more information than i would usually be able to get.

In an effort to trace this data I increased my system logging from 4:

```
[COLOR=#000000]**[FONT=Menlo]testuser@mysystem[/FONT]**[/COLOR][COLOR=#000000][FONT=Menlo]:[/FONT][/COLOR][COLOR=#5620F4][FONT=Menlo]**~/**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]$ cat /proc/sys/kernel/printk[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]4    4    1    7[/FONT][/COLOR]
**testuser@mysystem**[COLOR=#5620F4][FONT=Menlo][COLOR=#000000]:[/COLOR]**~/**[COLOR=#000000]$ sysctl kernel.printk[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]kernel.printk = 4    4    1    7[/FONT][/COLOR]
```

to 7:

```
**testuser@mysystem**[COLOR=#000000][FONT=Menlo]:[/FONT][/COLOR][COLOR=#5620F4][FONT=Menlo]**~/**[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]$ echo "7" | sudo tee /proc/sys/kernel/printk[/FONT][/COLOR][COLOR=#000000][FONT=Menlo][sudo] password for testuser: [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]7[/FONT][/COLOR]
**testuser@mysystem**[COLOR=#5620F4][FONT=Menlo][COLOR=#000000]:[/COLOR]**~/**[COLOR=#000000]$ sysctl kernel.printk[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]kernel.printk = 7    4    1    7[/FONT][/COLOR]
**testuser@mysystem**[COLOR=#5620F4][FONT=Menlo][COLOR=#000000]:[/COLOR]**~/**[COLOR=#000000]$ cat /proc/sys/kernel/printk[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]7    4    1    7[/FONT][/COLOR]
```

but I got no more detail.

*Question.*
How can I go about tracking down what command/process the system (kernel?) went through to get this data from my media? I'd like to get 'it' ([COLOR=#000000][FONT=Menlo]'57760311_A_USEFUL_NAME') [/FONT][/COLOR]into a variable somehow but i don't know how to trace it as my googlefu has not proved fruitful at this time.

I've checkout out 'lsblk', 'blkid', /etc/mtab to see what data they could give but they come back to UUID/LABEL data. I've looked at syslog, dmesg and journalctl to see if any more data there but its the same line as in syslog. I'm also aware of additional tools relating to udf (udftools) but loath to install something else when the system is already clearly able to extract the data I've shown above.

I can see from the log message that it's something to do with the UDF volume data, not necessarily the disc label but thats as far as I can get. Can anyone offer any pointers? Much appreciated if they can. Cheers 

my system is:

```

[COLOR=#000000][FONT=Menlo]Distributor ID:    Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Description:    Ubuntu 18.04.6 LTS[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Release:    18.04[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Codename:    bionic[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Kernel is: 4.15.0-163-generic
[/FONT][/COLOR]
```

---

### Post by TheFu on 2021-12-22
First, there must be 20 different types of optical media and optical media encryption.  Some of the industry standards are set by companies hostile towards Linux, so for those standards, everything had to be reverse engineered without access to any documentation.  In the industry, often there is a $100K "membership fee" to gain access to the standards documents. Small developers interested in these devices just won't pay for that access. Additionally, there are licenses around the use of the documents, such that leaking it or making it available to non-license holders would forfeit membership.  So, you pay $100K, gain access, but somehow another person leaks it - you are out of the club and they won't refund the dues.  If implementing software, there are requirements to fully implement the DRM portions too.  That often means that certain video streams have to be encrypted following specific HDCP standards - which is a different club to join with different membership fees.

There are multiple audio formats, multiple CD RW/RO formats, DVD RW/RO formats, BluRay formats, M-Disc formats, and HD-DVD formats.  Data formats are different from video and audio formats.

Do you see the complexity?  To my knowledge, there is only 1 program that can read BluRay video discs on Linux.  Reading DRM protected content off DVDs requires violating some laws in some countries.  The DMCA in the US being one.

As for automatic mounting, I have doubts that it can happen for copy-protected media.  For pure, unencrypted, data media, it shouldn't be hard.  You can get the label using lots of commands.  I don't have any optical drives left anymore (at least not working ones), so I cannot check this on that media, but
 **ls /dev/disk/by-label/** has all the known labels in the system with links to the actual file system.
Most of the time, the optical drive device will be fixed, say /dev/sdc so you can filter on that - bash can use globbing to accomplish it. 
Just store all the labels into a bash array, then you can loop over that array and do any other processing desired.
[https://tldp.org/LDP/abs/html/](https://tldp.org/LDP/abs/html/) has sections about arrays and loops.
Arrays: [https://tldp.org/LDP/abs/html/arrays.html](https://tldp.org/LDP/abs/html/arrays.html)
Globbing: [https://tldp.org/LDP/abs/html/globbingref.html](https://tldp.org/LDP/abs/html/globbingref.html)
Loops with arrays: [https://tldp.org/LDP/abs/html/loops1.html](https://tldp.org/LDP/abs/html/loops1.html) <--- the list of planets in their example is just an un-named array.

Most optical disc labels that I've seen over the years are all CAPS. I suspect this to be part of the standard, since some of those standards were created based on MS-DOS limitations.

If I need to do complex parsing of command output to get just a small part of the result, then I'll usually dump bash and switch to perl.  Ruby or Python would be just a good as perl, but I know perl.  If you need to see an example non-trivial bash program, check these out: [https://github.com/UbuntuForums](https://github.com/UbuntuForums)  The system-info script does lots of parsing using cut and sed.

---

### Post by Holger_Gehrke on 2021-12-23
There's a package named udftools which has a program named udfinfo. I have not tried it myself, but the man-page on github makes me think it might be useful for what you want.

Holger

---

