---
title: "How to fully erase and reformat my WinXP HDD with Ubuntu?"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by Rain on 2005-05-28
Good day everyone,
I am from Singapore. I have heard many praises for Ubuntu and so have downloaded and burn into a bootable CD. I am NEW to Linux. I have read books on Debian/GNU and Linux for Windows Addicts: A Twelve Step Program.
Unfortunately [COLOR=DarkGreen]i am still unable to fully format my hard disk so that i can get a clean disk to install this Ubuntu 5.04 into it. I do not want to have anymore Window OS in my disk already.[/COLOR]

[COLOR=DarkOrange]My system:
- Gigabyte 8SR533 motherboard
- Intel 1.7Ghz CPU
- Seagate 40GB HDD
(i have used Seagate HDD diagnostic tool to check it: error free) & (Connected to IDE1 on the mobo)
- NVidia Riva TNT2 M64 32MB Video Card
- Samsung 256MB DDR333 ram x02 = 512MB
(My memory is running at DDR266 though)
- 1.44" Floppy Drive
- LG DVD/CD ROM Drive
(Connected to my IDE2 on the mobo)
- PCI USB1.1
- D-Link 10/100 Eternet card
(D-Link is the only producer that supports Linux Kernel 2.4.x from what i found out in Singapore: Please correct me if iam wrong)
- HEC 300W PSU[/COLOR]

I apologise for my noob-ness. I have tried to search a solution in this forum and search engine for 2 weeks already, but in vain. Can any member/seniors kindly advice me or point me to a reference site. I appreciate greatly.

Regards,
Rain.

---

### Post by netrattler on 2005-05-28
When you install from the CD it can automatically wipe out windows and setup your partitions for you if you ask it to take over the whole disk. Unless you want a custom partition setup then all you have to do is select the manual partition option.

Joe

---

### Post by Rain on 2005-05-29
Thank you very much, netrattler. I have sucessfully installed Ubuntu on my HDD.
You have answered my concern. I have read several posts on the issue that Window OS will not be completely removed by linux, thus causing their HDD unable to boot up.

I met another problem. During loading, there is one FAIL item:
  > temporary failure in name resolution

I went to the Device Manager, and passed my sound, video and mouse tests, but the screen took a loooong time to load, when it reached Network test.. and the NEXT button is disabled.. I have no choice but to select Cancel to exit.

Sigh... I will try to look around in this forum and the net. If i cannot solve it, i will post back here. I thank you again for your assistance.

---

### Post by netrattler on 2005-05-29
Sounds like it's not either picking up your network card correctly or you are have a DNS problem. If you go to System -> Administration -> Networking -> do you have eth0 in your list of connections and does it say it is active. I'm guessing that your running broadband if you click on the DNS tab does it list the DNS servers of your ISP. Also can you browse the web from firefox, try typing in [www.yahoo.com](www.yahoo.com), if it wont accept this try entering the ip of the site like this and see if it brings there site up [http://68.142.226.40](http://68.142.226.40) , We can work from there.

Joe

---

### Post by Rain on 2005-05-30
Good day to you, netrattler, do you mind if i were to address you as Joe?

    Yes I have read and searched for what you mentioned, regarding DNS concern.
I [COLOR=Red]cannot access [www.yahoo.com](www.yahoo.com) [/COLOR] but i [COLOR=Red]can access through [http://68.142.226.40](http://68.142.226.40)[/COLOR]. So i did a search in the textbox provided in yahoo search engine in firefox and I met the same problem: "www.yahoo.com cannot be found, please check the name and try again".

    Very Interesting. So i did a ping and realised that i can ping to ANY ip addresses but not to the domain names. So i searched around in other linux forums. Some people have met such problem as I have encountered now.
[COLOR=Blue]1) [http://www.neowin.net/forum/lofiversion/index.php/t321752.html](http://www.neowin.net/forum/lofiversion/index.php/t321752.html)
2) [http://www.togaware.com/linux/survivor/Networking.shtml](http://www.togaware.com/linux/survivor/Networking.shtml)
3) [http://ubuntuforums.org/archive/index.php/t-9860.html](http://ubuntuforums.org/archive/index.php/t-9860.html)
4) [http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)[/COLOR]
The 3rd site, described a scenario very similar to my case. Unfortuately their replies were incomplete. 

    Alright, I am using a D-Link DFE-538TX 10/100 ethernet card, and I have a Aztech 4 port ADSL router(with built-in modem). I used a RJ45 cross-cable to connect to this router and access the internet. It was working fine while I was in WinXP. Since I can access the internet through the ip address, i assumed that the network card and router are working.

> If you go to System -> Administration -> Networking -> do you have eth0 in your list of connections and does it say it is active. I'm guessing that your running broadband if you click on the DNS tab does it list the DNS servers of your ISP 
    Yes I am using broadband and my network card has been installed successfully by Ubuntu without having me to install its driver :grin:  , and No it does not list out my DNS servers of my ISP (I am using 512K broadband plan from pacnet singapore). So I went to Networking and activate eth0 by manually configuring its ip address, subnet mask and default gateway. I used to [COLOR=DarkGreen]set WinXP to obtain ip address(DHCP enabled) and DNS server address automatically[/COLOR], and everything worked fine. 
[COLOR=DarkOrange]Btw, do you know what i can use to edit *.conf files?[/COLOR] [http://undernetlinuxnewbie.org/wiki/index.php/Resolv.conf](http://undernetlinuxnewbie.org/wiki/index.php/Resolv.conf) stated that i can use vi, vim, pico, nano, joe or a gui editor. So in order for me to add/remove programs, i will have to use apt-get right so as to install the above editors to allow me to edit *.conf files? By default, does Ubuntu installed apt-get? And of the 6 editors mentioned, which one do you recommend me to use?

    I apologise and appreciated netrattler aids and to all other members as well. I am seeking to improve my knowledge in linux, and I do not want to go back to Windows ever again. If anyone of you know of a good site that explains linux in simple terms especially with [COLOR=DarkOrange]images guide[/COLOR], I believed all of us, newbies, will benefit from your recommendation.  :wink:

---

### Post by grim42 on 2005-05-30
Hi there,

Don't know if this will help, but try setting the DNS Nameserver in the networking configuration to the same IP as your default gateway (router IP).

This assumes that the router is actually handling the connection to your ISP and you're not using PPPoE on your Linux system.

Otherwise you'll need to find out your ISP's DNS server IP addresses.

Greg

---

### Post by netrattler on 2005-05-30
Ok here is the DNS information for your ISP, I already tried them out and they work.
So go to System -> Administration -> Networking -> click on the DNS tab -> for the DNS Servers click the add button type this 203.120.90.40  -> click the add button again and type this 192.169.33.3 -> for the Search Domains click the add button and type this pacific.net.sg -> Then just click the ok button startup firefox and see if you can now browse by domain names instead of IP addresses. Hope this helps.

Joe

---

### Post by Rain on 2005-05-31
Thank you Greg and Joe for your assistance. Though i have not tried out Greg suggestion but it sounds sensible.
[COLOR=DarkOrange]Joe, you have my heartfelt thanks.[/COLOR] I will hope that I will get strong and help others like you have help me.

This is my msn, contact me anytime in the night, [email]playstuff642@hotmail.com[/email]

Best regards,
Wilson.

---

