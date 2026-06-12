---
title: "[SOLVED] trouble installing Brother DCP310CN Printer/Scanner"
date: 2008-10-20
forum: General Help
---

### Post by bosun1000 on 2008-10-20
Help please I have installed my Brother DCP310CN all in one Printer in Ubuntu Hardy Heron.
The printer works fine I have acquired the driver 
brscan-skey-0.2.1-1.i386.deb for the scanner from the Brother website I have installed Xsane but I just can't get Ubuntu to recognise my scanner I go the route of Applications/graphics/xsane image scanner and a box pops up with "no devices available". Can somebody please help. I am an absolute begginer and have not touched windows XP for 2 months now!  
Thanks in advance
Bosun

---

### Post by plucky on 2008-10-20
> **bosun1000 said:**
> Help please I have installed my Brother DCP310CN all in one Printer in Ubuntu Hardy Heron.
The printer works fine I have acquired the driver 
brscan-skey-0.2.1-1.i386.deb for the scanner from the Brother website I have installed Xsane but I just can't get Ubuntu to recognise my scanner I go the route of Applications/graphics/xsane image scanner and a box pops up with "no devices available". Can somebody please help. I am an absolute begginer and have not touched windows XP for 2 months now!  
Thanks in advance
Bosun

According to the Brother website,you need to download the brscan2-0.2.4-0.i386.deb package for 32-bit installation or brscan2-0.2.4-0.amd64.deb for 64-bit installation.


See this [link](http://solutions.brother.com/linux/en_us/instruction_scn1a.html) for instructions to install.Do not miss the instructions in step 5 to enable a normal user to get permissions to use the scanner.


Good Luck

---

### Post by bosun1000 on 2008-10-20
Thanks for you reply I followed the instructions you supplied (my Printer is network connected not USB But I found the right instructions on the Brother site) I now have an improvement insomuch I no longer get a pop up with "No devices available" I now get error box message "Failed to open device 'brother2:net1;dev0': invalid argument." Will you please help again?
Thanks Bosun 


> **plucky said:**
> According to the Brother website,you need to download the brscan2-0.2.4-0.i386.deb package for 32-bit installation or brscan2-0.2.4-0.amd64.deb for 64-bit installation.


See this [link](http://solutions.brother.com/linux/en_us/instruction_scn1a.html) for instructions to install.Do not miss the instructions in step 5 to enable a normal user to get permissions to use the scanner.


Good Luck

---

### Post by plucky on 2008-10-20
> **bosun1000 said:**
> Thanks for you reply I followed the instructions you supplied (my Printer is network connected not USB But I found the right instructions on the Brother site) I now have an improvement insomuch I no longer get a pop up with "No devices available" I now get error box message "Failed to open device 'brother2:net1;dev0': invalid argument." Will you please help again?
Thanks Bosun

I haven't installed a network printer/scanner,but did you follow the instructions for setting up the network scanner?

Did you install **sane-utils** in synaptic?

Do you know the IP address of the printer/scanner?

Have you also installed the scan-key-tool? (See instructions on Brother website)


```
Add network scanner entry

    $ brsaneconfig2 -a name=SCANNER model=DCP-540CN ip=192.168.3.3
    $

Confirm network scanner entry

    $ brsaneconfig2 -q | grep SCANNER
      0 SCANNER             "DCP-540CN"         I:192.168.3.3
    $

```

Good Luck

---

### Post by bosun1000 on 2008-10-21
Did you install **sane-utils** in synaptic? ......Yes already installed

Do you know the IP address of the printer/scanner?.... Yes entered

Have you also installed the scan-key-tool? (See instructions on Brother website)....Yes already installed
Also have already entered the code for "Add network scanner entry"
and "Confirm network scanner entry"

on trying to use scanner (Applications/graphics/xsane image scanner)a box appears "Scanning for devices" then I just wait, after about a minute an error box appears "Failed to open device 'brother2:net1;dev0': invalid argument" 
I just don't understand whats wrong apart from a stupid mistake on my part consequently I'm pulling out whats left of my hair!
Thanks Bosun


> **plucky said:**
> I haven't installed a network printer/scanner,but did you follow the instructions for setting up the network scanner?

Did you install **sane-utils** in synaptic?

Do you know the IP address of the printer/scanner?

Have you also installed the scan-key-tool? (See instructions on Brother website)


```
Add network scanner entry

    $ brsaneconfig2 -a name=SCANNER model=DCP-540CN ip=192.168.3.3
    $

Confirm network scanner entry

    $ brsaneconfig2 -q | grep SCANNER
      0 SCANNER             "DCP-540CN"         I:192.168.3.3
    $

```

Good Luck

---

### Post by plucky on 2008-10-21
Can you open a terminal and ```
ping <scanner IP address>
``` to see if you can access the network address.

Also can you post output from a terminal of ```
brsaneconfig2 -q | grep SCANNER
```

As a troubleshooting tool,although it is not recommended for everyday use, try to run xsane in super user mode ```
sudo xsane
``` and see what that gives you.

Is it possible to plug in the USB cable to your computer to see if the software is installed correctly? That would eliminate a software driver problem and would then be a network problem.
If you can use the USB connection,you have to do one more step to get the correct permissions.
See this [**link**](http://solutions.brother.com/linux/en_us/instruction_scn1c.html)


Good Luck

---

### Post by bosun1000 on 2008-10-21
john@Home:~$ ping <scanner IP address>
bash: syntax error near unexpected token `newline'
john@Home:~$ 



john@Home:~$ brsaneconfig2 -q | grep SCANNER
  0 SCANNER             "DCP-310CN"         I:192.168.001.065
john@Home:~$ 


ran xsane in super user mode popup box says scanning for devices then nothing.

I feel sure the software has installed properly. I could put in usb cable but it is almost impossible to get to at the moment due to computer fixed in desk will try if I absolutely have to but only as last resort  

Thanks for staying with me I will keep trying but I'm beginning to feel out of my depth as I am only 2 months into ubuntu and am a silver surfer who is completely self taught!
Bosun

[

QUOTE=plucky;6005724]Can you open a terminal and ```
ping <scanner IP address>
``` to see if you can access the network address.

Also can you post output from a terminal of ```
brsaneconfig2 -q | grep SCANNER
```

As a troubleshooting tool,although it is not recommended for everyday use, try to run xsane in super user mode ```
sudo xsane
``` and see what that gives you.

Is it possible to plug in the USB cable to your computer to see if the software is installed correctly? That would eliminate a software driver problem and would then be a network problem.
If you can use the USB connection,you have to do one more step to get the correct permissions.
See this [**link**](http://solutions.brother.com/linux/en_us/instruction_scn1c.html)


Good Luck[/QUOTE]

---

### Post by plucky on 2008-10-21
> john@Home:~$ ping <scanner IP address>
bash: syntax error near unexpected token `newline'


That would be ```
ping -c 5 192.168.001.065
``` to see if the printer/scanner responds with five responses.

> john@Home:~$ brsaneconfig2 -q | grep SCANNER
0 SCANNER "DCP-310CN" I:192.168.001.065

This seem to indicate that the network scanner is installed.

---

### Post by bosun1000 on 2008-10-22
Oh dear this doesn't look good! Could I have the wrong IP address? (its what the printer told me) if so how do I find the right one?  Any more pointers?

john@Home:~$ ping -c 5 192.168.001.065
PING 192.168.001.065 (192.168.1.53) 56(84) bytes of data.
From 192.168.1.64 icmp_seq=2 Destination Host Unreachable
From 192.168.1.64 icmp_seq=3 Destination Host Unreachable
From 192.168.1.64 icmp_seq=4 Destination Host Unreachable
From 192.168.1.64 icmp_seq=5 Destination Host Unreachable

--- 192.168.001.065 ping statistics ---
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 4000ms
, pipe 3
john@Home:~$ 

Thanks again
Bosun




> **plucky said:**
> That would be ```
ping -c 5 192.168.001.065
``` to see if the printer/scanner responds with five responses.



This seem to indicate that the network scanner is installed.

---

### Post by plucky on 2008-10-22
> john@Home:~$ ping -c 5 192.168.001.065
[color=red]PING 192.168.001.065 (192.168.1.53) 56(84) bytes of data.[/color]
From 192.168.1.64 icmp_seq=2 Destination Host Unreachable
From 192.168.1.64 icmp_seq=3 Destination Host Unreachable
From 192.168.1.64 icmp_seq=4 Destination Host Unreachable
From 192.168.1.64 icmp_seq=5 Destination Host Unreachable



That doesn't look as though it is the correct IP address.

Please post output of a terminal window of ```
ifconfig
```

Can you login to your router? That should tell you what IP addresses it can see.

---

### Post by bosun1000 on 2008-10-22
john@Home:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:55:4f:20  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe55:4f20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6384067 (6.0 MB)  TX bytes:1143145 (1.0 MB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:876 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43800 (42.7 KB)  TX bytes:43800 (42.7 KB)

john@Home:~$ 


I probably can login to my router if I can find how? does the above help?

Regards Bosun 





> **plucky said:**
> That doesn't look as though it is the correct IP address.

Please post output of a terminal window of ```
ifconfig
```

Can you login to your router? That should tell you what IP addresses it can see.

---

### Post by plucky on 2008-10-22
> inet addr:192.168.1.64


It shows your computer IP address as above so,in all probability,the address specified by your printer is correct.I don't know why you cannot ping that address as that should respond to the ping.

Also I assume the printer is working,and will also be on that address,so why it is not responding has got me baffled.

What does ```
brsaneconfig2 -p
``` give you,as that is the command to use the sane communication to the scanner?

Also try ```
ping 192.168.1.65
``` without the loading zeroes on the last two numbers.

Also reinstall the scanner without the leading zeroes in the IP address
```
brsaneconfig2 -r SCANNER
brsaneconfig2 -a name=SCANNER model=DCP-540CN ip=192.168.1.65
```

Good Luck

---

### Post by bosun1000 on 2008-10-22
I don't know why but in terminal as instructed I entered: 

```
brsaneconfig2 -r SCANNER
brsaneconfig2 -a name=SCANNER model=DCP-540CN ip=192.168.1.65
```

and I now have a working scanner! I would love to know why (particularly as I have a DCP310CN not a DCP 540 CN ) so I can learn for next time or perhaps I should take a crash course in code syntax!
Anyway I can't thank you enough for your patience. 

Kind Regards
Bosun



> **plucky said:**
> It shows your computer IP address as above so,in all probability,the address specified by your printer is correct.I don't know why you cannot ping that address as that should respond to the ping.

Also I assume the printer is working,and will also be on that address,so why it is not responding has got me baffled.

What does ```
brsaneconfig2 -p
``` give you,as that is the command to use the sane communication to the scanner?

Also try ```
ping 192.168.1.65
``` without the loading zeroes on the last two numbers.

Also reinstall the scanner without the leading zeroes in the IP address
```
brsaneconfig2 -r SCANNER
brsaneconfig2 -a name=SCANNER model=DCP-540CN ip=192.168.1.65
```

Good Luck

---

### Post by plucky on 2008-10-22
> **bosun1000 said:**
> I don't know why but in terminal as instructed I entered: 

```
brsaneconfig2 -r SCANNER
brsaneconfig2 -a name=SCANNER model=DCP-540CN ip=192.168.1.65
```

and I now have a working scanner! I would love to know why (particularly as I have a DCP310CN not a DCP 540 CN ) so I can learn for next time or perhaps I should take a crash course in code syntax!
Anyway I can't thank you enough for your patience. 

Kind Regards
Bosun

Good to hear!!!

I think the problem was you put the IP address with leading zeroes which for some reason the network doesn,t seem to like.


i.e "ping 192.168.1.65" is not the same as "ping 192.168.001.065"

As for the DCP-540CN,that was my mistake, you can rerun the two commands again,the first one to remove the scanner and the second on to install it again,but with the correct model=DCP-310CN.The important part is the IP address has to be correct.Also you can change the name to whatever you want.


Please mark the thread as solved using the [color=red]Thread Tools[/color] at the top of the page.Only the OP=Original poster can do this.


Good Luck

---

### Post by bosun1000 on 2008-10-22
One last thing would you please write me the code to remove the DCP-540CN
and reinstall the DCP310CN.
Thank you 
Bosun


> **plucky said:**
> Good to hear!!!

I think the problem was you put the IP address with leading zeroes which for some reason the network doesn,t seem to like.


i.e "ping 192.168.1.65" is not the same as "ping 192.168.001.065"

As for the DCP-540CN,that was my mistake, you can rerun the two commands again,the first one to remove the scanner and the second on to install it again,but with the correct model=DCP-310CN.The important part is the IP address has to be correct.Also you can change the name to whatever you want.


Please mark the thread as solved using the [color=red]Thread Tools[/color] at the top of the page.Only the OP=Original poster can do this.


Good Luck

---

### Post by plucky on 2008-10-23
> **bosun1000 said:**
> One last thing would you please write me the code to remove the DCP-540CN
and reinstall the DCP310CN.
Thank you 
Bosun

```
brsaneconfig2 -r SCANNER
``` will remove the scanner
```
brsaneconfig2 -a name=SCANNER model=DCP-310CN ip=192.168.1.65
``` will add it back with the correct model.
```
brsaneconfig2 -q | grep SCANNER
``` will show you if the scanner is installed.

Good Luck

---

