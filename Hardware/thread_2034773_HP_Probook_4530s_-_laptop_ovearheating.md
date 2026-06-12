---
title: "HP Probook 4530s - laptop ovearheating"
date: 2012-07-29
forum: Hardware
---

### Post by trulynon on 2012-07-29
Hi everyone,

I facing with very annoying problem, mean it overheating! I have installed Jupiter and CPU Freq scaling indicator and this will drop down temps apropx 2-3°C.

However, the temperatures are still high! The highest temperature point I've seen was 75 degrees, which is only 10 degrees less then a critical level (85°C).

Even now, after two hours of browsing Web CPU temp is very high. 

[img]http://www3.picturepush.com/photo/a/8844056/img/8844056.png[/img]
[img]http://www2.picturepush.com/photo/a/8844060/640/Anonymous/Screenshot-from-2012-07-29-07%3A14%3A49.png[/img]

I have HP Proobok 4530s with Intel HD 3000 graphics integrated card and i3 processor. I'm working on Ubuntu 12.04 64-bit. Today I updated kernel to 3.2.24-030224-generic with no changes. Fan is always running and laptop is very hot. It simply impossible to work. Touching the laptop is like touching a heater!

Of course laptop is clean and work flawlessly on Widows 7 (never experienced an overheating problem). I'd like to stay on Ubuntu, but I cant get rid of the heating. 

I've been reading a hundreds of post regarding overheating problems. Installed Laptop-Mode-Tools, modified Grub ("quiet splash pcie_aspm=force") with no results. This drive me crazy and finally If I cant get a solution I'll have to back to Windows, since I can properly work on this laptop when is hot. Any suggestion will appreciated. Thanks

Mariusz

---

### Post by meijer.o on 2012-07-29
I have exactly the same laptop. I never noticed any overheating with ubuntu 12.4 - gnome-shell. Batterylife is about the same as windows.

Best regards,

Otto Meijer

---

### Post by trulynon on 2012-07-29
Hi, 
 
HP Probook 4530s were also distributed with ATI graphic card, however mine dosen't have an additional ATI card. Perhaps your has it? I read it somewhere that in Idle all 8 processor cores are running and producing lot of heat. In Windows Intel used additional drivers (?) to disable "non needed" cores. Exclusion of additional cores decrease power consumption and hence less heat generated.
 
Many owners of HP laptops (also with Probook) struggling with an overheating. So your particular example is very interesting. Can you provide more details about your specs?
 
I have also tried to run on this laptop Linux Mint from a flash drive and there wasn't any problem with heating. By far I have to stay with Windows 7. Actually I wrote this post now from Windows 7. I wish that someone find a proper fix for that.

---

### Post by meijer.o on 2012-07-29
Here you are , you have te same laptop as I have, it has only two cores, sandybridge i3

lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
23:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
23:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
23:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
24:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
25:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
26:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +43.0°C  (crit = +128.0°C)
temp2:         +0.0°C  (crit = +128.0°C)
temp3:        +50.0°C  (crit = +128.0°C)
temp4:        +48.0°C  (crit = +128.0°C)
temp5:        +35.0°C  (crit = +128.0°C)
temp6:         +0.0°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:         +0.0°C  (crit = +128.0°C)

These are certainly OK.

Best regards,

Otto Meijer

---

### Post by ahallubuntu on 2012-07-29
See if there is a newer BIOS version available from HP; if so, I would install the update in Windows 7 and see if that helps.

---

### Post by in0cula on 2012-08-06
I have hp 4530s like trulynon with just the HD 3000, and I noticed the overheating with ubuntu 12.04, the left part of the mousepad is very warm, with win 7 it doesn't happen....same problem with fedora 17 gnome shell all updated with 3.5 kernel....so i really don't know why, any help?

---

### Post by trulynon on 2012-08-06
> **in0cula said:**
> I have hp 4530s like trulynon with just the HD 3000, and I noticed the overheating with ubuntu 12.04, the left part of the mousepad is very warm, with win 7 it doesn't happen....same problem with fedora 17 gnome shell all updated with 3.5 kernel....so i really don't know why, any help?

This has something to do with an Intel drivers IMHO. I quit with an Ubuntu because of this issue. There's no solution of this problem so far. I'm on Windows 7 recently and my problems with an overheating aren't exits.

I'd like to start using Ubuntu again, however, the overheating is a major problem for my laptop (and I assume that for many as well). Can some one from an Ubuntu builders assist to get rid of this issue? Thanks

---

### Post by in0cula on 2012-08-06
I wuold like to be a linux user but I had to switch to win as well, in linux overheating in win 7 cool. :(

---

### Post by trulynon on 2012-08-10
> **ahallubuntu said:**
> See if there is a newer BIOS version available from HP; if so, I would install the update in Windows 7 and see if that helps.

That was a good advice, to be honest. I did updated BIOS to a newer version downloaded from [here]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=5060880&prodNameId=5060882&swEnvOID=4053&swLang=13&mode=2&taskId=135&swItem=ob-107194-1"). After installing Ubuntu 12.04 LTS again, I noticed that temperatures aren't so hight as before.

[img]http://www4.picturepush.com/photo/a/8944007/1024/Anonymous/Screenshot-from-2012-08-10-18%3A05%3A16.png[/img]

The notebook isn't that hot and I can easily work on it. So far so good, I would say. I planning to use Ubuntu per a couple of days and test it.

---

### Post by in0cula on 2012-08-11
> **trulynon said:**
> That was a good advice, to be honest. I did updated BIOS to a newer version downloaded from [here]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=5060880&prodNameId=5060882&swEnvOID=4053&swLang=13&mode=2&taskId=135&swItem=ob-107194-1"). After installing Ubuntu 12.04 LTS again, I noticed that temperatures aren't so hight as before.

[IMG]http://www4.picturepush.com/photo/a/8944007/1024/Anonymous/Screenshot-from-2012-08-10-18%3A05%3A16.png[/IMG]

The notebook isn't that hot and I can easily work on it. So far so good, I would say. I planning to use Ubuntu per a couple of days and test it.

Thank you, I didn't notice that there were a new BIOS update, hope this will solve the issue. let you know.

---

### Post by trulynon on 2012-08-11
I hope this will help to you as well. Apart of the update BIOS to a latest version, I noticed that when I have used Chromium browser my notebook was getting hotter. I get rid of Chromium and I keep the FireFox as a my main browser. I've started to get a positive results. So, my advice would be to keep FireFox as your main Internet browser. I will report any other thoughts soon.

So far is good! The notebook is running about 6 hours constantly with browsing the web only, OpenOffice and PDF editing. Recent temperatures are:

```
mariusz@mariusz-HP-ProBook-4530s:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  (crit = +128.0°C)
temp2:         +0.0°C  (crit = +128.0°C)
temp3:        +31.0°C  (crit = +128.0°C)
temp4:        +43.0°C  (crit = +128.0°C)
temp5:        +27.0°C  (crit = +128.0°C)
temp6:         +0.0°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:         +0.0°C  (crit = +128.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +49.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +45.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +48.0°C  (high = +80.0°C, crit = +85.0°C)
```The ridiculous 60°C never been achieved, even if I have opened 40 tabs. I still have installed Jupiter and set up on "POWER ON DEMAND". "Power saver" gives me a better results, however, I was unable to watch YouTube videos (due to a power limits?) . I can still feel the warm from my notebook, but it's really less noticeable and I can easily work on.

Edit:

Temperatures with an only open Firefox:

[img]http://www2.picturepush.com/photo/a/8953015/1024/Anonymous/last.png[/img]

Regards, Mariusz

---

### Post by in0cula on 2012-08-12
Yesterday i did the bios update, I just installed fedora 17 KDE, made all the updates and I notice that the temperature of the left side of the touchpad is decreased a lot but still warm,  I can say that now i think i can use linux, anyway with windows 7 the laptop is perfect cool. 

I'm with the kernel 3.5.1-1.fc17.x86_64 , I'll let you know how the thing going.

thx bye

PS. my temps are almost exactly as yours.

---

### Post by trulynon on 2012-08-12
> **in0cula said:**
> Yesterday i did the bios update, I just installed fedora 17 KDE, made all the updates and I notice that the temperature of the left side of the touchpad is decreased a lot but still warm,  I can say that now i think i can use linux, anyway with windows 7 the laptop is perfect cool. 

I'm with the kernel 3.5.1-1.fc17.x86_64 , I'll let you know how the thing going.

thx bye

PS. my temps are almost exactly as yours.


That's good to know :)  My kernel version is **3.2.0-29-generic**. The temperature of the left side of the touch pad is now OK to me.  A really noticeable warm has gone. This is my third day with Ubuntu and I'm not going back to Windows. The warm heating is not so annoying as I experienced before and battery life is now increased up to 4 hours. That's good news, I'd says that working time on a battery is even longer then on Windows. 

Have you tried installed Jupiter and play with the [power consumption settings]("http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1")? This might decrease temperature lot more, however, my temperatures now are OK for me. I'd like to decrease temperature to at least 40°C, but I think isn't possible. The lower level how I managed to get on Windows was 43°C, so I'm quite happy now and I really believe that future bring for us a lot of changes in this case and finally someone solve this issue. I'll look forward your thoughts.

Recent temps (notebook is on at least 14 hours):

```
 mariusz@mariusz-HP-ProBook-4530s:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  (crit = +128.0°C)
temp2:         +0.0°C  (crit = +128.0°C)
temp3:        +34.0°C  (crit = +128.0°C)
temp4:        +48.0°C  (crit = +128.0°C)
temp5:        +31.0°C  (crit = +128.0°C)
temp6:         +0.0°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:         +0.0°C  (crit = +128.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +49.0°C  (high = +80.0°C, crit = +85.0°C)
Core 0:         +46.0°C  (high = +80.0°C, crit = +85.0°C)
Core 1:         +49.0°C  (high = +80.0°C, crit = +85.0°C)
```

---

### Post by trulynon on 2012-08-15
Hi all,

I would like to add a couple of more thoughts how the things are going now.  First of all, I have to say I think that my existing overheating problem has been solved. Temperatures are usually under  50 degrees and notebook is not so hot as was before. Fan is running constantly, however, I have no problem with this. An overall performance is just decent. I will recommend to use a FireFox and jupiter and of course make sure that you have the latest BIOS version. I will go deep and deep into Ubuntu and I think that this is the future of the OS. Thanks for advices, I really appreciated. 

Btw. I mark the thread solved. Thanks

---

