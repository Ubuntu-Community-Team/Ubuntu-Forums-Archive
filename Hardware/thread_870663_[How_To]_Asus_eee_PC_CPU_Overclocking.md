---
title: "[How To] Asus eee PC CPU Overclocking"
date: 2008-07-26
forum: Hardware
---

### Post by tinny on 2008-07-26
At first I was a little disappointed with the performance of my Asus eee PC (701 4G) running Ubuntu, but after applying the following CPU overclocking script my system has become much more responsive.

Under a standard Ubuntu install your CPU will only operate at a maximum of 630.100 MHz with a FSB speed of 70MHz. After applying the following instructions your machine will operate at the designed CPU speed of 900MHz with a FSB speed of 100MHz.

Here are the steps to take for CPU overclocking.

1. Download "eee-overclocking-install.sh" (attached to this post).

2. Open a terminal and navigate to the downloaded file.

3. Next you will want to give the file execute permissions (so you can run the script) and then run the script.

```

chmod u+rwx eee-overclocking-install.sh
sudo ./eee-overclocking-install.sh

```

The script will run for a while...

4. Restart your machine.

5. Restart you machine and double click the new "Overclock" icon on your desktop. This will activate the CPU overclocking (you will need to do this eveytime you want CPU overclocking).

6. You are DONE!!!

EDIT: Please use the script in post #8, DO NOT use the one below

---

### Post by w1zard on 2008-09-18
I'm using the Netbook Remix of eeeUbuntu, which doesn't have a desktop as such. The installer seems to have worked, and I've restarted - how do I go about manually starting the overclock without the shortcut?

The shortcut is not in the Desktop folder, from what I can see.

---

### Post by DaVince21 on 2008-09-18
Oh, that's simple. The script *doesn't* make one.

Anyone know what was supposed to be in that desktop script, so it can be created/attached manually?

EDIT: tried [these](http://www.sampletheweb.com/2007/12/30/overclock-your-asus-eee-pc-fsb-on-ubuntu/) instructions instead, but they result in the system locking up with weird glitched-up graphics. I'm using the -eee kernel from Array.org, could this be the cause (since I accidentally overwrote its eee.ko file with the custom compiled one).

EDIT after reinstalling eee kernel: the overwrite didn't seem to be the problem. Maybe it'll overclock if I use the generic kernel, but then I'll probably lose some speed and hardware compatibiliy...

---

### Post by tinny on 2008-09-18
Sorry, I missed out the overclock utilities. 

I believe that this needs to be added to the script.

> 
echo "## Installing Overclock Utilities ##"
wget "http://eee.ricey.co.uk/files/eee/oc.sh"
wget "http://eee.ricey.co.uk/files/eee/ocn.py"
wget "http://eee.ricey.co.uk/files/eee/Overclock.desktop"
sudo mv oc.sh /usr/bin
sudo chown root:root /usr/bin/oc.sh
sudo chmod +x /usr/bin/oc.sh
sudo mv ocn.py /usr/bin
sudo chown root:root /usr/bin/ocn.py
sudo chmod +x /usr/bin/ocn.py
mv Overclock.desktop ~/Desktop
echo "## Done ##"


Ill add this to the original script.

---

### Post by tinny on 2008-09-18
Here is the new script.

---

### Post by Teetdiro on 2008-09-18
bump the thread up.A bald man took a seat in a beauty shop. "How can I help you?" asked the stylist. "I went for a hair transplant," the guy explained, "but I couldn't stand the pain. If you can make my hair look like yours without causing me any discomfort, I'll pay you $5,000.""No problem," said the stylist, and he quickly shaved his head.------------The WOW gold Online Store, Open 24/7 Looking to buy [wow gold](http://www.u4game.com), Items or Accounts? You would find the cheapest gold here. We always online 24 hours a day, 7 days a week, any questions regarding [world of warcraft gold](http://www.u4game.com), powerleveling,wow leveling ,[warcraft gold](http://www.u4game.com), just talk to our representatives using our 24/7 live chat service.[world of warcraft gold](http://www.u4game.com/world-of-warcraft-gold.html),[wow leveling](http://www.u4game.com/Wow_Power_Leveling.html),

---

### Post by Calmatory on 2008-09-18
Anyone care to test how much they overclock at best? (by editing the oc.sh file)

---

### Post by DaVince21 on 2008-09-19
The new script doesn't work either because of CR+LF line encoding. Don't forget to convert it to LF before you run it!

---

### Post by tinny on 2008-09-19
:oops: oops, I edited it in windows.

Try this one :) (third time lucky)

---

### Post by DaVince21 on 2008-09-19
It works like a charm! Thank you very much. The vids that used to stutter a bit now play at full speed, and more awesomeness like that! :D

You should suggest to add this as a package in the Array.org repository or something, since it makes (temporary/optional) overclocking a breeze. :)

---

### Post by Miksu90 on 2008-10-20
im wondering why very soon after that "overclocked " message it downclokcs my processor back to 630 mhz? how can i fix this ?

---

### Post by tinny on 2008-10-20
> **Miksu90 said:**
> im wondering why very soon after that "overclocked " message it downclokcs my processor back to 630 mhz? how can i fix this ?

It ramps up the speed when it is needed. Try doing some sort of processor intensive task and then check the clock frequency.

---

### Post by glotz on 2008-10-20
I think it would be nice to mention the actual tools used in the first post.

Also, there's a typo in [http://eee.ricey.co.uk/files/eee/ocn.py](http://eee.ricey.co.uk/files/eee/ocn.py)

"This improves performance and [color=red]increase[/color] heat generation."

And the word CPU is spelled sometimes all CAPS, sometimes not.

And the word Hertz is abreviated Hz, note the capitalization.

:)

---

### Post by Miisu6 on 2008-10-30
Hey.

I'm cpmpletely new to Linux and system modifying aswell. I did all You described here and ended up with a screen full of... well colorful boxes :D
Don't know how to describe it, like parts of desktop were scrambled around on the screen and no response from the computer after that. Restart fixed it. 
I have changed RAM on my eee PC 701 4G (with Ubuntu eee version installed).
Might that be the cause?

Would like to get the overclock working...
Any advice?

---

### Post by kbkntk on 2008-12-14
> **tinny said:**
> :oops: oops, I edited it in windows.

Try this one :) (third time lucky)
using the file in #8 works great on my eeepc 701, too. thanks for that info.
furthermore i just discovered a tool called **emifreq-applet** via synaptic. that does the same thing, is easier to install and one can switch between several modes (automatic cpu control, constant fequencies or powersave mode)! :)

---

### Post by vagelism on 2008-12-28
Hello ...
After the script installation I have some extra files in my desktop.
Should I delete them? Or is better to make them hidden in order not to watch them seating there.
THANK YOU

---

### Post by tinny on 2008-12-28
> **vagelism said:**
> Hello ...
After the script installation I have some extra files in my desktop.
Should I delete them? Or is better to make them hidden in order not to watch them seating there.
THANK YOU

You can delete them. Just dont delete the "Overclock" icon on the desktop.

---

### Post by fastlegs on 2009-05-12
I tried all those files but none of them worked! They did install but my desktop is empty! Is there command I can use in terminal?

---

### Post by threepenpals on 2009-05-16
I followed the instructions posted (including downloading the 3rd script), but failed to notice a performance increase on a en eee 701 running Jaunty.

I checked dmesg and found that it was still reporting the cpu running at 630 MHz.

Any advice for getting the program to correctly overclock in this situation?

Barring that, any advice for completely removing the programs installed by the script and reversing whatever changes it made would be greatly appreciated.  Thanks.

---

### Post by blackest_knight on 2009-10-24
-there is a bit of a bug in the eee.c file which messes things up with make on later kernels "proc_root undefined" in three places which you can replace with NULL successfully and over clock successfully glx gears gains about a 1/3rd going to 100 mhz front bus.

the attached file needs to be renamed eee.c and that will build successfully.

trouble with the earlier scripts they appear to work bt if the compile failed there is no eee.ko and no overclocking. don't forget it will need a rebuild with every kernel update :)

---

### Post by rcpinchey on 2009-12-17
Just got this working in Karmic. Use the above eee.c file, but you'll also have to comment out two lines that attempt to set the "owner" member of a structure, which has now been removed. Once that's done, it builds and runs fine.

---

### Post by somudrog on 2009-12-19
Which 2 lines are you referring to exactly? Perhaps you could just post the new file ? :)

Also, do you just place eee.c in the same directory as the script and then just run it again?

---

### Post by olds1978 on 2010-02-01
> **tinny said:**
> At first I was a little disappointed with the performance of my Asus eee PC (701 4G) running Ubuntu, but after applying the following CPU overclocking script my system has become much more responsive.

Under a standard Ubuntu install your CPU will only operate at a maximum of 630.100 MHz with a FSB speed of 70MHz. After applying the following instructions your machine will operate at the designed CPU speed of 900MHz with a FSB speed of 100MHz.

Here are the steps to take for CPU overclocking.

1. Download "eee-overclocking-install.sh" (attached to this post).

2. Open a terminal and navigate to the downloaded file.

3. Next you will want to give the file execute permissions (so you can run the script) and then run the script.

```

chmod u+rwx eee-overclocking-install.sh
sudo ./eee-overclocking-install.sh

```The script will run for a while...

4. Restart your machine.

5. Restart you machine and double click the new "Overclock" icon on your desktop. This will activate the CPU overclocking (you will need to do this eveytime you want CPU overclocking).

6. You are DONE!!!

EDIT: Please use the script in post #8, DO NOT use the one below



Hi 
I downloaded the fil but how can i make it work?? Its not a EXE fil,

---

### Post by olds1978 on 2010-02-01
Hi 
I downloaded the fil but how can i make it work?? Its not a EXE fil,
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8759346") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8759346")

---

### Post by echo_head on 2010-02-11
Um yeah, so its really late over here and I've been up for a while, being an utter linux noob didn't help matters either... Anyhoo, I went ahead and installed the first scipt instead of the one in post 8 like I was supposed to.  Whoopsy frickin daisy!  \\:D/  Can't seem to find much info on uninstalling scripts.  Is there a way or does this mean that I have to fresh install ubuntu again?

---

### Post by new2eee on 2010-03-26
just picked up a sparsely used eeepc 4g surf 701 for about 100$, and im currently running this script. Hoping to bump up the performance a lil. 

BTW the reason why i joined this forum is because of the OP's great work. Thanks a lot man! this makes life real easy for people making a foray into linux, after bashing their heads against windows. 

I love Ocing.. though on my main rig.. but the possibility of doing it on eeepc is too tempting to let go!!! lol!

Thanks again.. 

running the script on ubuntu netbook remix.

---

### Post by new2eee on 2010-03-26
Its alive!! its alive!! it works! thanks man...

---

### Post by AgentGreen508 on 2010-07-21
hey sorry to bother everyone.. been trying to get overclocking in linux for month's now 
with no results ...

ive tried to compile the eee.c module in ubuntu lucid...
and in koala i always get the same errors tried this script 
and here's what it said "same as all other times"
[FONT=monospace]
make -C /lib/modules/2.6.32-23-generic/build M=/home/agentgreen/Downloads/eeepc-linux/module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/agentgreen/Downloads/eeepc-linux/module/eee.o
/home/agentgreen/Downloads/eeepc-linux/module/eee.c: In function &#8216;eee_proc_init&#8217;:
/home/agentgreen/Downloads/eeepc-linux/module/eee.c:399: error: &#8216;proc_root&#8217; undeclared (first use in this function)
/home/agentgreen/Downloads/eeepc-linux/module/eee.c:399: error: (Each undeclared identifier is reported only once
/home/agentgreen/Downloads/eeepc-linux/module/eee.c:399: error: for each function it appears in.)
/home/agentgreen/Downloads/eeepc-linux/module/eee.c:404: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/home/agentgreen/Downloads/eeepc-linux/module/eee.c:421: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/home/agentgreen/Downloads/eeepc-linux/module/eee.c: In function &#8216;eee_proc_cleanup&#8217;:
/home/agentgreen/Downloads/eeepc-linux/module/eee.c:442: error: &#8216;proc_root&#8217; undeclared (first use in this function)
make[2]: *** [/home/agentgreen/Downloads/eeepc-linux/module/eee.o] Error 1
make[1]: *** [_module_/home/agentgreen/Downloads/eeepc-linux/module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [all] Error 2
cp: cannot stat `eee.ko': No such file or directory
## Done ##
## Unblacklisting i2c-i801 module ##
./eee-overclocking-install.sh: 17: cannot open /etc/modprobe.d/blacklist: No such file
mv: cannot stat `blacklist.tmp': No such file or directory
chown: cannot access `/etc/modprobe.d/blacklist': No such file or directory
## Done ##
## Updating /etc/modules ##

yeah but when i click icon desktop to start it up i get no good luck
it says it overclocks my pc but without having the module install...

but system doesn't improve... like it should ove 
ive tried many bios's also but they wont boot up linux after 
update only windows.wich is what im avoiding... was trying the 8804
but no luck yet... Im actually thinkning ove using amibios editor soon
and copying the line of code for overclocking from the beta bios's too the new bios's but would probably brick my eee

any help would be apreciated as this is the only issue making my ubuntu
usage a downer... Downclocking overclocking and fan control...
to extend every inch of battery

thanks everyone 
asus eeepc 4g with 2gb ddr 667mhz kingston ram
running 10.04
[/FONT]

---

### Post by MWP on 2010-08-11
As a quick update to this...

Im running Kernel 2.6.32 which allows native over/under clocking of the eeePC using the standard cpufreq-set tool.
No building of the above attached extra modules is required.

The automatic governors like ondemand wont work though due to the transition latency being too high.

Speed setting has been verified by using nbench to benchmark different CPU speeds.

Some info on my blog here: [http://eeedash.mwp.id.au/2010-08/emdebian-on-eeepc-701/](http://eeedash.mwp.id.au/2010-08/emdebian-on-eeepc-701/)

```

root@eeepc:~# cpufreq-info
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.00 ms.
  hardware limits: 113 MHz - 900 MHz
  available frequency steps: 113 MHz, 225 MHz, 338 MHz, 450 MHz, 563 MHz, 675 MHz, 788 MHz, 900 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 113 MHz and 900 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 900 MHz (asserted by call to hardware).
  cpufreq stats: 113 MHz:0.00%, 225 MHz:0.00%, 338 MHz:0.00%, 450 MHz:0.00%, 563 MHz:0.00%, 675 MHz:0.00%, 788 MHz:0.00%, 900 MHz:100.00%

```

---

### Post by calimocho on 2010-08-13
> **MWP said:**
> As a quick update to this...

Im running Kernel 2.6.32 which allows native over/under clocking of the eeePC using the standard cpufreq-set tool.
No building of the above attached extra modules is required.

The automatic governors like ondemand wont work though due to the transition latency being too high.

Speed setting has been verified by using nbench to benchmark different CPU speeds.

Some info on my blog here: [http://eeedash.mwp.id.au/2010-08/emdebian-on-eeepc-701/](http://eeedash.mwp.id.au/2010-08/emdebian-on-eeepc-701/)



Can you go into more detail on your setup?  This isn't working for me :-( I looked at your blog post but didn't see where it answered the question.  Thanks 
```

$ cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 0.00 ms.
```

---

### Post by jeremy4465 on 2010-09-28
> **w1zard said:**
> I'm using the Netbook Remix of eeeUbuntu, which doesn't have a desktop as such. The installer seems to have worked, and I've restarted - how do I go about manually starting the overclock without the shortcut?

The shortcut is not in the Desktop folder, from what I can see.
sorry to bump it w1zard all that the script makes is a shortcut to a file called oc.sh
but the command in it is gksu oc.sh

---

### Post by mshenrick on 2011-04-19
I ran the script manually so I could see any errors. when it comes to make, I get error 2

```
make -C /lib/modules/2.6.38-7-generic/build M=/tmp/eeepc-linux/module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-7-generic'
  CC [M]  /tmp/eeepc-linux/module/eee.o
/tmp/eeepc-linux/module/eee.c: In function ‘eee_proc_init’:
/tmp/eeepc-linux/module/eee.c:399:43: error: ‘proc_root’ undeclared (first use in this function)
/tmp/eeepc-linux/module/eee.c:399:43: note: each undeclared identifier is reported only once for each function it appears in
/tmp/eeepc-linux/module/eee.c:404:21: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/tmp/eeepc-linux/module/eee.c:421:18: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/tmp/eeepc-linux/module/eee.c: In function ‘eee_proc_cleanup’:
/tmp/eeepc-linux/module/eee.c:442:31: error: ‘proc_root’ undeclared (first use in this function)
make[2]: *** [/tmp/eeepc-linux/module/eee.o] Error 1
make[1]: *** [_module_/tmp/eeepc-linux/module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-7-generic'
make: *** [all] Error 2

```

---

### Post by philcolbourn on 2011-05-18
eee.ko module takes a bit of editing to make it compile, I found.

Three places &proc_root had to be changed to NULL, and two places the whole line about .owner had to be commented out.

(Sorry, I'm not on it right now).

It then compiled under debian squeeze.

But I also found that someone else made a newer version that seemed to compile better - search for a 0.3 version.

But after all this, I found p4_clocking module worked far easier. 

In my case I wanted to save power but changing the clock did not do this.

---

### Post by David Welch on 2011-08-01
For some strange reason I am not able to download all of the required files. here is the message I get


**Installing Overclock Utilities
--2011-08-01 17:23:46--  [http://eee.ricey.co.uk/files/eee/oc.sh](http://eee.ricey.co.uk/files/eee/oc.sh)
Resolving eee.ricey.co.uk... 94.76.252.34
Connecting to eee.ricey.co.uk|94.76.252.34|:80... connected.
HTTP request sent, awaiting response... 500 Internal Server Error
2011-08-01 17:23:47 ERROR 500: Internal Server Error.

--2011-08-01 17:23:47--  [http://eee.ricey.co.uk/files/eee/ocn.py](http://eee.ricey.co.uk/files/eee/ocn.py)
Resolving eee.ricey.co.uk... 94.76.252.34
Connecting to eee.ricey.co.uk|94.76.252.34|:80... connected.
HTTP request sent, awaiting response... 500 Internal Server Error
2011-08-01 17:23:47 ERROR 500: Internal Server Error.

--2011-08-01 17:23:47--  [http://eee.ricey.co.uk/files/eee/Overclock.desktop](http://eee.ricey.co.uk/files/eee/Overclock.desktop)
Resolving eee.ricey.co.uk... 94.76.252.34
Connecting to eee.ricey.co.uk|94.76.252.34|:80... connected.
HTTP request sent, awaiting response... 500 Internal Server Error
2011-08-01 17:23:47 ERROR 500: Internal Server Error.



Why is this happening?

---

### Post by sirvismara on 2012-02-16
Hi guys!

Sorry for my noobness but I need some help.

I followed the instruction on the first post and in the end terminal said "installation succesful, please restart" (or something like this). I restarted but nothing appared on my empty desktop... what can I do?

I am running lubuntu 11.10

Please, don't answer me "read the thread", I red it and I don't understood it...otherwise I wouldn't ask for help :D

Thank you!

S

---

### Post by Yharooer on 2013-03-29
> **sirvismara said:**
> Hi guys!

Sorry for my noobness but I need some help.

I followed the instruction on the first post and in the end terminal said "installation succesful, please restart" (or something like this). I restarted but nothing appared on my empty desktop... what can I do?

I am running lubuntu 11.10

Please, don't answer me "read the thread", I red it and I don't understood it...otherwise I wouldn't ask for help :D

Thank you!

S

Same. Linux Mint 14.

---

### Post by mx6josue on 2013-06-05
> **Yharooer said:**
> Same. Linux Mint 14.

Same here Linux Mint 15

---

