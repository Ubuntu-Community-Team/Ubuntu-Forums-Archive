---
title: "Can't browse the internet"
date: 2008-07-22
forum: General Help
---

### Post by lieja on 2008-07-22
i have gutsy gibon and xp on my laptop.the problem is why i cant browse the internet frm linux? i guess nothing goes wrong with connectivity because the ping was successfull. i've configure the eth0 with dhcp..please help me..anything wrong with firefox?

---

### Post by fsmithred on 2008-07-22
What did you ping? Was it a number or a name? Is your computer behind a router, or is it directly connected to the modem?

Is this the same problem that's preventing you from installing software from the repository?
[http://ubuntuforums.org/showthread.php?t=864920](http://ubuntuforums.org/showthread.php?t=864920)

---

### Post by lieja on 2008-07-23
this is the output frm a command i've run..

eth0      Link encap:Ethernet  HWaddr 00:1D:72:58:D9:E0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe58:d9e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5692 (5.5 KB)  TX bytes:12822 (12.5 KB)
          Interrupt:17

---

### Post by ookamisan on 2008-07-23
Thats probably the result from ```
ifconfig eth0
```.
What internet connection do you have? And how are you connected physically to the internet? Directly? Or do you have a router? What does "ipconfig /all" in Windows XP tell you? Is the IPv4 address 192.168.1.2 as well?

---

### Post by lieja on 2008-07-23
im using broadband connection. my laptop is connected directly with DSL modem.give me 5 minute..let me check the ip first

---

### Post by lieja on 2008-07-23
yup..the ip is the same, 192.168.1.2

---

### Post by ookamisan on 2008-07-23
Okay, next task for you ;)

Compare the default gateway settings.
Under windows I think you can see it in the ipconfig /all output

Under linux:```
route | grep default
```
The first IP listed after the "default" is your default gateway. Should be the same because of DHCP.

Second Task:
ping your gateway.

Third Task:
ping 72.14.207.99

Fourth Task:
ping google.com

If Third works but Fourth not, then it might be a DNS problem.

Have you tried accessing the ubuntu repositories via synaptic or the update manager?

Does firefox work with an Ip address like 72.14.207.99 (it's a google server)

---

### Post by lieja on 2008-07-23
OK..i've do what u ask me:)

the command give me default ip 0.0.0.0..if im not mistaken..this is loopback address..rite? then..i ping the ip as u ask. the ping is succesful..is it the rite command to check the default gateway?

the ping frm terminal shows no prob both ip and domain name are successfully reply frm server but the problem that i just see is when i browse in firefox..now,i able to go to google page frm server ip that u gave me b4..what makes me wonder..several websites still can be browse with their domain name.but still i couldnt browse smoothly coz its really slow..

so..do u c the problem yet??:confused:

thanks 4 ur attention

---

### Post by fsmithred on 2008-07-23
Slow browsing makes me think that the problem is not your computer. Are you sharing your connection with anyone, or are you running any other programs that access the internet? (like bittorrent, for example) 

And this might sound like a stupid question, but does your dsl modem have an antenna on the back? (for you folks who are laughing right now, I want you to know that my dsl modem has a wireless router built into it, and the default is for wireless to be on and wide open.) If it does have one, you should either turn it off or secure it. Try browsing to 192.168.1.1 and see if you get to a router utility.

Another thing you might try is changing the nameserver in /etc/resolv.conf. Try 4.2.2.2 instead of what's there, and see if it speeds things up. In case that's not clear, the only line you need in resolv.conf would be:
```
nameserver 4.2.2.2
```

---

### Post by lieja on 2008-07-24
im not sharing the connection with anyone and my problem right now is i cant browse the internet in ubuntu. if the problem is about the connection..why the browser just work properly in windows(xp).i juz wanna try to make the browsing works rite now..b4 i can download or using other program or anything..

btw..i've check my modem.there's no wireless function..

ok..i'll try the last thing u mention to me..then i'll reply about the result..thanks:)

---

### Post by lieja on 2008-07-24
how to access the resolve.conf file..the permission is denied:(

---

### Post by fsmithred on 2008-07-24
You have to use sudo to edit system files. Maybe the easiest way to do it would be to open network manager, click on the DNS tab, and enter the nameserver there.

Another thing you might try it to use a different web browser, such as Opera or Epiphany, and see if it works any better.

---

### Post by lieja on 2008-07-25
i've already try using the sudo gedit command to edit the file but it's an empty file.how can i install other browser like opera without internet connection:(

---

### Post by plucky on 2008-07-25
> **lieja said:**
> i've already try using the sudo gedit command to edit the file but it's an empty file.how can i install other browser like opera without internet connection:(


The file is **/etc/resolv.conf** not resolve.conf and should contain something like **nameserver 192.168.11.1**

The command to edit that file is ```
gksudo gedit /etc/resolv.conf
```

Good Luck

---

### Post by lieja on 2008-07-25
thanks plucky for ur command.so that i can access the file and edit the nameserver to 4.2.2.2 as what's told by fsmithred..it works. now..i can browse frm ubuntu..may i know what juz happened fsmithred? what's the 4.2.2.2 address? anyway..thanks all..now i juz have to deal with installing software..i've so many problems with package manager..hope..u guys can help me on this later:popcorn:

---

### Post by fsmithred on 2008-07-25
That's a public DNS server. I assume you were using your ISP's nameserver before editing that file. If you'd been using none, you would not have been able to browse to a named website, you'd have to use the IP number. 

And since you could get to some websites by name and some only by number, I assume that the problem is with your ISP's nameserver. I've had that problem, and trying to explain it to tech support at the ISP was fun. They couldn't understand that they were the ones with the problem.

Maybe your package manager will work now.

---

### Post by lieja on 2008-07-26
yes..ur right..my package manager seems to work well now.there r updates n i can start download software now. thanks a bunch:)

---

