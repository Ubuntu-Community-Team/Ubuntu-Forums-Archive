---
title: "Compile AR2427 Wireless Chip on Ubuntu 10.04"
date: 2010-05-13
forum: Hardware
---

### Post by ekeyme on 2010-05-13
[COLOR=#000000][FONT=Arial]**                          [COLOR=Red]UPDATE:[/COLOR] Now there is a much easy way to solve this problem. A much GUI control way and suitable for all the Atheros 9K wireless chips: see **[/FONT][/COLOR][post from vagrale13]("http://ubuntuforums.org/member.php?u=952139") [COLOR=#000000][FONT=Arial][B] -->[[COLOR=RoyalBlue] http://ubuntuforums.org/showthread.php?t=1564278 .[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1564278")
this update is the final one, because more and more new distributions of Linux will default support this wireless chip. I will not update this post any more. Pardon me!!

Compile AR2427 Wireless Chip on Ubuntu 10.04 [/B][/FONT][/COLOR]  [Original text]("http://docs.google.com/document/edit?id=1eVo-IG3YE_KB5kqIgcJkvMbVdLWs--cgZyOU__cxkpg&hl=en")
[COLOR=#000000][FONT=Arial]Recently[/FONT][/COLOR][COLOR=#000000][FONT=Arial]**, **[/FONT][/COLOR][COLOR=#000000][FONT=Arial]the Lucid Lynx Ubuntu 10.04 released. Many funs maybe can’t wait to install & use it on their [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]own PC just like me too. But my experience may not be  very happy, thought the new version is very cool with its friendly user interface and faster staring up.  Because my wireless care AR2427 [ 168c:002c ] on Asus EeePC 900HA  doesn’t work. In some days google-ing and waiting the  solution coming from Ubuntu Bug Team & the forum postings. Finally I now get out of my wifi trouble. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]It seams that the kernel version( 2.6.32.22-generic )  now Ubuntu 10.04 used does not su-  pport this maybe new-released wireless chip. I googled some news saying  the AR2427        [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][ 168c:002c ] will be support in the [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_2.6.33+ kernel  releasing_[/FONT][/COLOR]]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33.2-lucid/CHANGES")[COLOR=#000000][FONT=Arial].  So it means Ubuntu maybe can autofixing AR2427-ath9k chip in the next  coming( maybe the next next ) kernel update( there have been some  relative[/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_ Bug noticed in  the Lunchpad_[/FONT][/COLOR]]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux-backports-modules-2.6.32/+bug/521967")[COLOR=#000000][FONT=Arial]. and you can wait for the update time coming but the waiting  time is very boring or you can use the fellow solution to get a  pre-wifi-working before the next( doesn’t be sure ) kernel update.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Maybe many guys may be  likely to prefer using the [/FONT][/COLOR][COLOR=#000000][FONT=Arial] Ndiswrapper [/FONT][/COLOR][COLOR=#000000][FONT=Arial] to fixing the AR2427 in the linux OS  due to the simple build directly using the wifi driver from windows. But  a friend of mine told me it may not work perfectly since wifi speed  may have a little crap. some others may choose the mdwifi to get AR2427  work, because I had try a time on Ubuntu 10.04 beta2 and failed due to  my lacking skill.  So I now use the [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Compat Wireless Drivers [/FONT][/COLOR][COLOR=#000000][FONT=Arial]to solve my wifi  trouble witch really runs perfectly on my EeePC  900HA. The step follow is How I Get my wifi work.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Out put of the comman ’ $ lspci ’ from my PC on Ubuntu 10.04. [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] ……[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]01:00.0 Ethernet  controller [0200]: Atheros Communications Atheros AR8121/AR8113/AR8114  PCI-E Ethernet Controller [1969:1026] (rev b0)    [/FONT][/COLOR][COLOR=#3d85c6][FONT=Arial]*&#65288;wire NIC&#65289;*[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]02:00.0 Network  controller [0280]: Atheros Communications Inc. Device [[/FONT][/COLOR][COLOR=#ff0000][FONT=Arial]168c:002c[/FONT][/COLOR][COLOR=#000000][FONT=Arial]] (rev 01)[/FONT][/COLOR]
[COLOR=#3d85c6][FONT=Arial]*&#65288;wireless&#65289;*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] …… &#65281;[/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_more detail_[/FONT][/COLOR]]("https://answers.launchpad.net/ubuntu/+question/109155")

[COLOR=#000000][FONT=Arial]In order to compile  the driver you’ll need at least a C compiler and the make utility,  so you firstly make sure you have install them in your Ubuntu. If not you can get it with the apt-get to [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]install the package just as:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]      [COLOR=Red]sudo  apt-get install build-essential[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]You’ll also need your kernel headers  installed, but they most is likely to be installed  by default. Double  check that the directory /lib/modules/`uname -r`/build  exists. If not please get it [/FONT][/COLOR]
[COLOR=Red][FONT=Arial]*sudo apt-get install linux-headers-`uname -r`*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#the mark ” ` ” is located on the top of Tab key on the keyboard[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Download compat wireless drivers from [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_here_[/FONT][/COLOR]]("http://wireless.kernel.org/download/compat-wireless-2.6/")[COLOR=#000000][FONT=Arial]. I used the [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_compat-wireless-2010-04-26.tar.bz2_[/FONT][/COLOR]]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-26.tar.bz2")[COLOR=#000000][FONT=Arial] , also you can choose  it by yourself because it may update everyday and the latest version  always is  [/FONT][/COLOR][[COLOR=#000099][FONT=Arial]_compat-wireless-2.6.tar.bz2_[/FONT][/COLOR]]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2")[COLOR=#000000][FONT=Arial].[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Extract your Download file  and cd into the resulting directory.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]          [COLOR=Red]tar -xjvf[/COLOR] [/FONT][/COLOR][COLOR=#0b5394][FONT=Arial]name-download-file[/FONT][/COLOR][COLOR=#0b5394][FONT=Arial]destination-directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]          [COLOR=Red]cd[/COLOR] [/FONT][/COLOR][COLOR=#0b5394][FONT=Arial]destination-directory+name-download-file[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The AR2427 chip is  covered by the[/FONT][/COLOR][COLOR=#000000][FONT=Arial] ath9k[/FONT][/COLOR][COLOR=#000000][FONT=Arial] driver, so we firstly select the modules ath9k for this  driver[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  [COLOR=Red]./scripts/driver-select  ath9k[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]then make and install[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  [COLOR=Red]make[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#make sure this step  without notice errors, If error occur, you’d better copy it and google  in the google to #get answer. or you can select another version compat  wireless drivers.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial] [COLOR=Red]sudo  make install[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#wait ... ...[/FONT][/COLOR]

[COLOR=Red][FONT=Arial]sudo make unload[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#this step maybe can  cancel, when you cancel it and the next step printing error. then you  can add this #step before  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo modprobe [/FONT][/COLOR][COLOR=#ff0000][FONT=Arial]**ath9k.**[/FONT][/COLOR]

[COLOR=Red][FONT=Arial]sudo modprobe [/FONT][/COLOR][COLOR=Red][FONT=Arial]**ath9k**[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]after the above step  your wifi device may appear under iwconfig, you can check you have  compile AR2427 in the right way, run modinfo:[/FONT][/COLOR]
[COLOR=Red][FONT=Arial]modinfo ath9k [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#in the output, there  must be a line [/FONT][/COLOR][COLOR=#ff0000][FONT=Arial]**RED**[/FONT][/COLOR][COLOR=#000000][FONT=Arial] word like the fellow  post[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][I]
ilename:   /lib/modules/2.6.32-18-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko[/I][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*license: Dual  BSD/GPL*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*description: Support for Atheros 802.11n wireless LAN cards.*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*author:  Atheros Communications*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*srcversion: A50A865BAAB45E03B5852F0*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*alias:  pci:v0000168Cd0000002Esv*sd*bc*sc*i**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*alias:  pci:v0000168Cd0000002Dsv*sd*bc*sc*i**[/FONT][/COLOR]
[COLOR=#ff0000][FONT=Arial]***alias:  pci:v0000168Cd0000002Csv*sd*bc*sc*i****[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*alias:  pci:v0000168Cd0000002Bsv*sd*bc*sc*i**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*alias:  pci:v0000168Cd0000002Asv*sd*bc*sc*i**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*alias:  pci:v0000168Cd00000029sv*sd*bc*sc*i**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*alias:  pci:v0000168Cd00000027sv*sd*bc*sc*i**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*alias:  pci:v0000168Cd00000024sv*sd*bc*sc*i**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*alias:  pci:v0000168Cd00000023sv*sd*bc*sc*i**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*depends:  ath9k_hw,mac80211,led-class,ath,cfg80211,ath9k_common*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*vermagic:  2.6.32-18-generic SMP mod_unload modversions 586*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*parm:  debug:Debugging mask (uint)*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*parm: nohwcrypt:Disable hardware encryption  (int)*[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]If that occured,  CONGRATULATIONS! then reboot you PC, sening it whether the wifi device  appears in the iwconfig or in the NetworkManager( on the Top right of  desk ).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]If  failed, you can uninstall it whetherever you like by [/FONT][/COLOR]
[COLOR=Red][FONT=Arial]sudo make  unload[/FONT]
[/COLOR] [COLOR=Red][FONT=Arial]sudo make  uninstall [/FONT][/COLOR]

**[COLOR=#000000][FONT=Arial]THANKS TO [/FONT][/COLOR][[COLOR=#000099][FONT=Arial][B]_James Little_**[/FONT][/COLOR]]("http://www.jameslittle.me.uk/")[[COLOR=#000099][FONT=Arial]**_The Asus Eee PC  1005PE & Ubuntu_**[/FONT][/COLOR]]("http://www.jameslittle.me.uk/asus-1005pe-ubuntu/")[/B]

---

### Post by leifew on 2010-05-15
That worked well on my ASUS Eee PC 1005P running EasyPaesy 1.6. Thanks a lot :)

---

### Post by der_gabe on 2010-05-22
Thanks so much for this post!
It worked like a charm for me! :KS
I had tried "ndiswrapper" and even a custom-built kernel, both to no avail. I had all but given up hope, but then I found your post on how you solved the problem on your Eee PC 900HA and since I have the exact same model I thought it was worth to at least try.
Now it works, at least I can see the card, it's managed by NetworkManager and  it detects some wireless networks close by. I will test it with a network I have access to, as soon as possible.

---

### Post by ekeyme on 2010-06-05
ahh!! ^_^,:P  before I fixing it on my EeePC, I have the same experience like yours. 
maybe the step follow can more simply fix it now, but I never try that on my pc before, someone who may like geekly try.

- ENABLE wlan in BIOS.
- Download new version of kernal image from here :
[http://kernel]("http://kernel/") dot  ubuntu.com/~kernel-ppa/mainline/daily/

for example :
$ wget [http://kernel]("http://kernel/") dot  ubuntu.com/~kernel-ppa/mainline/daily/2010-05-12-lucid/linux-image-2.6.34-999-generic_2.6.34-999.201005121008_i386.deb
$ sudo dpkg -i  linux-image-2.6.34-999-generic_2.6.34-999.201005121008_i386.deb

Reboot.

Atheros AR2427 Card  will/may be now  recognised.
Enjoy.

---

### Post by jiaolu on 2010-06-11
this is really nice post.Solve my problem for the 1005pe..Thanx 
bump

---

### Post by SWT_nux on 2010-06-16
thank you for the post, looking for to trying it out.

I will say, this is why Linux(Ubuntu)fails to significantly gain ground.
I dont care what kind of fancy interface or neat tricks you can do, wifi is an essential, especially in a netbook. all three of my laptop/netbooks have had to do some decent amount of fiddling.

Its very frustrating to get a new netbook, wipe and partition, install windoze(everything smooth), install unr and as usual no wifi. really tempted to uninstall, but then I remember how much I like buntu and will wait 'til they are done with neat interfaces and get to work on some basic network connectivity.

sorry, rough day..............

---

### Post by SWT_nux on 2010-06-16
worked like a charm on the asus 1001p. thanks again.
definitely easier than messing with those darn broadcom 43's use to be.
now to but this thing through its paces.

---

### Post by aaronyyz on 2010-07-05
Just purchased an eee 1005P as I'm moving countries soon and will it will be a perfect travelling PC. Thanks to your post, wireless is working perfectly! No way could I have done this by myself.

---

### Post by Rave Gloves on 2010-09-15
please someone make this simple.
Extract your Download file and cd into the resulting directory.
tar -xjvf name-download-filedestination-directory
cd destination-directory+name-download-file 

i put:
 tar -xjvf compat-wireless-2.6.tar.bz2-downloads-rachel

and i hasn't worked so im not sure what im doing wrong :(

---

### Post by saif_held on 2010-12-01
Could this work for an Atheros AR5001?

---

### Post by ekeyme on 2010-12-11
> **saif_held said:**
> Could this work for an Atheros AR5001?
Sorry, Haven't fixed AR5001. I think you only need to change the [drives version] fore [[COLOR=#000099][FONT=Arial]_here_[/FONT][/COLOR]]("http://wireless.kernel.org/download/compat-wireless-2.6/")[COLOR=#000000][FONT=Arial]. The fixing main way is the same.

And I think my this presentation was out date, because nowadays kernel has change. I'd like you to look for a better solution. Good Luck!
[/FONT][/COLOR]

---

### Post by paulobergo on 2010-12-20
Hi!
Great post! Solve my HBNB-1401 HBuster T4400 under Ubuntu9.04-64!
But I still have a problem:
Every time I turn on my notebook, I need to do:
#modprobe ath9k
to bring up the wireless...
How to configure Ubuntu to auto-start the ath9k?
Tkx!

---

### Post by ekeyme on 2011-12-08
Sorry, not very good at this. But I think there is a new GUI way to fix this.  See this post UPDATE.

---

