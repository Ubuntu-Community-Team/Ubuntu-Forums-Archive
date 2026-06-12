---
title: "Suspend: when/where is the lid opened/closed?"
date: 2008-06-30
forum: Hardware
---

### Post by bogoliubov on 2008-06-30
Hello. I have suspend to ram working a bit. When choosing suspend from the gnome-menu or powerbutton, it works without any issues. 
But if I close the lid, it usually doesn't work. Nor if I first suspend the laptop using the powerbutton, then closing the lid and finally opening it again...
Sometimes this works, but never twice in a row. Usually, when opening the lid again, the computer is in some strange state from which I can only escape by holding the power button until the computer stops...

So, it seems there are some issues with the lid itself. Where can I see if the lid (acpi device) is triggered?

---

### Post by phidia on 2008-06-30
/etc/default/acpi-support is the file & settings you're looking for.
Getting this to work right though seems a little tricky from threads I've read. 
I think some hardware isn't well supported for suspend but that's MO.
I like the guide [here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Release_Candidate_on_a_ThinkPad_T61") on laptop settings/configuration but it's obviously not all inclusive. I think you need to provide your hardware specs and/or search those.

---

### Post by bogoliubov on 2008-06-30
> **phidia said:**
> /etc/default/acpi-support is the file & settings you're looking for.
Getting this to work right though seems a little tricky from threads I've read. 
I think some hardware isn't well supported for suspend but that's MO.
I like the guide [here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Release_Candidate_on_a_ThinkPad_T61") on laptop settings/configuration but it's obviously not all inclusive. I think you need to provide your hardware specs and/or search those.

I've already had a look in the /etc/default/acpi-support file, but there is nothing in it that relates to the "lid", at least not from what I understood.



I'll have a look at the wiki. Thanks!

---

### Post by bogoliubov on 2008-07-01
Ok, so I've figured out that when the lid is closed/opened, the /etc/acpi/lid.sh script is run. But how can I figure out if it is run also in the case when the computer locks up?

The /etc/acpi/lid.sh script checks if gnome-power-manager or kpowersave is running. If so, the script will simply exit. So how does the computer get suspended through this script?? I guess gnome-power-manager does something, but how does it know when an event (lid opening/closing) occurs, if it isn't called upon by the /etc/acpi/lid.sh??

I'd be really grateful all the help I can get on this!

---

### Post by User479857 on 2008-07-01
I was composing [this]("http://ubuntuforums.org/showthread.php?t=845962") thread when you were bumping your thread up to the top, but it would seem we have similar problems. I would be curious to know if you have the EXACT same problem. :)

---

### Post by bogoliubov on 2008-07-01
Hello. No, it doesn't seem like we have the exact same problem. In my case, sometimes it works to close the lid, but usually not.

I have a Clevo M540N laptop, running Hardy.

---

### Post by bogoliubov on 2008-07-02
No one? I can't be the only one on this...!?

---

### Post by bogoliubov on 2008-07-08
This is odd. Many users seem to experience suspend/resume problems?!

---

### Post by phidia on 2008-07-08
You didn't provide your laptops specs. Providing just the model/maker means we need to search that to get the cpu/gpu/wireless card/ect. in my experiance those three things are really important to whether suspend works or not. Nvidia & ATI gpus seem to have more suspend issues then intel.
This will be heresey but I found that opensuse 11.0 works very well on my HP-even the main speakers being muted when the earphones are plugged in works! Suspend and resume works too!

---

### Post by bogoliubov on 2008-07-09
I have a Clevo M540N. I'm not sure what spec to give, but here goes...:

CPU: Core 2 Duo T7200
Chipset/GFX: Intel GMA 945

lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:07.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
05:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

What more info can be useful here? Anything about the ACPI stuff? I don't know how to obtain that...

---

### Post by phidia on 2008-07-10
> but never twice in a row. Usually, when opening the lid again, the computer is in some strange state from which I can only escape by holding the power button until the computer stops...

So, it seems there are some issues with the lid itself. Where can I see if the lid (acpi device) is triggered?

Can you get to CLI or tty after this happens? Press Alt+Ctrl+F1 or F1 thru F6 and type dmesg 
There should be some output there about what happened.
You might also try to restart x by Alt+Ctrl+backspace.

---

### Post by bogoliubov on 2008-07-11
Hello. No, it doesn't work. Actually, pressing CapsLock won't light up the LED, so I guess it really crashes...

Thanks for helping!

---

### Post by phidia on 2008-07-11
Take a look at your /var/log/acpid file and perhaps message or kernel log too.
Something in the logfiles should reveal what is happening.

I've had my own issues with suspend using an HP Pavilion laptop. Thought I had it beat but after a kernel update it all went dysfunctional again. 
I'm providing two links I'm reading now for handing suspend/acpi issues in linux. 
Check them out [here]("http://www.advogato.org/article/913.html") (a mostly informative treatise) & [here]("http://www.linux.com/feature/114220") (usable methods, ideas, and scripts).

Added later (plus see above edits): [This thread]("http://ubuntuforums.org/showthread.php?t=630919") might be useful for people having suspend acpi issues. I think it's unfortunately hard to keep all this info organized in some meaningful way. People find parts of the answer but as more questions are asked that info gets buried.

---

### Post by bogoliubov on 2008-07-11
Thanks alot for the help. I have looked in the /var/log/acpid file before, but not understood where things have gone wrong...
I'll have a look at the links!

---

### Post by bogoliubov on 2008-07-13
So here's the output from /var/log/acpid on three occasions; one when nothing happened after a LID close, one were everything went OK and finally one when the computer crashed upon LID close.

To me, it seems that there are different LID numbers when everything is OK and when nothing happens...

/var/log/acpid when closing LID and nothing happens:
[Sat Jul 12 20:47:24 2008] received event "button/lid LID 00000080 00000001"
[Sat Jul 12 20:47:24 2008] notifying client 5480[111:123]
[Sat Jul 12 20:47:24 2008] notifying client 5648[0:0]
[Sat Jul 12 20:47:24 2008] executing action "/etc/acpi/lid.sh"
[Sat Jul 12 20:47:24 2008] BEGIN HANDLER MESSAGES
[Sat Jul 12 20:47:24 2008] END HANDLER MESSAGES
[Sat Jul 12 20:47:24 2008] action exited with status 0
[Sat Jul 12 20:47:24 2008] completed event "button/lid LID 00000080 00000001"
[Sat Jul 12 20:47:41 2008] received event "button/lid LID 00000080 00000002"
[Sat Jul 12 20:47:41 2008] notifying client 5480[111:123]
[Sat Jul 12 20:47:41 2008] notifying client 5648[0:0]
[Sat Jul 12 20:47:41 2008] executing action "/etc/acpi/lid.sh"
[Sat Jul 12 20:47:41 2008] BEGIN HANDLER MESSAGES
[Sat Jul 12 20:47:41 2008] END HANDLER MESSAGES
[Sat Jul 12 20:47:41 2008] action exited with status 0
[Sat Jul 12 20:47:41 2008] completed event "button/lid LID 00000080 00000002"



##############################
/var/log/acpid when closing LID and everything worked:
(Done after closing LID and nothing happened)
[Sat Jul 12 20:49:38 2008] received event "button/lid LID 00000080 00000003"
[Sat Jul 12 20:49:38 2008] notifying client 5480[111:123]
[Sat Jul 12 20:49:38 2008] notifying client 5648[0:0]
[Sat Jul 12 20:49:38 2008] executing action "/etc/acpi/lid.sh"
[Sat Jul 12 20:49:38 2008] BEGIN HANDLER MESSAGES
[Sat Jul 12 20:49:38 2008] END HANDLER MESSAGES
[Sat Jul 12 20:49:38 2008] action exited with status 0
[Sat Jul 12 20:49:38 2008] completed event "button/lid LID 00000080 00000003"
[Sat Jul 12 20:50:57 2008] received event "processor CPU0 00000081 00000000"
[Sat Jul 12 20:50:57 2008] notifying client 5480[111:123]
[Sat Jul 12 20:50:57 2008] notifying client 5648[0:0]
[Sat Jul 12 20:50:57 2008] client has disconnected
[Sat Jul 12 20:50:57 2008] completed event "processor CPU0 00000081 00000000"
[Sat Jul 12 20:50:57 2008] received event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:50:57 2008] notifying client 5480[111:123]
[Sat Jul 12 20:50:57 2008] completed event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:50:57 2008] received event "battery BAT0 00000081 00000001"
[Sat Jul 12 20:50:57 2008] notifying client 5480[111:123]
[Sat Jul 12 20:50:57 2008] executing action "/etc/acpi/power.sh"
[Sat Jul 12 20:50:57 2008] BEGIN HANDLER MESSAGES
[Sat Jul 12 20:50:57 2008] END HANDLER MESSAGES
[Sat Jul 12 20:50:57 2008] action exited with status 0
[Sat Jul 12 20:50:57 2008] completed event "battery BAT0 00000081 00000001"
[Sat Jul 12 20:50:57 2008] client connected from 5648[0:0]
[Sat Jul 12 20:50:57 2008] 1 client rule loaded
[Sat Jul 12 20:50:58 2008] received event "processor CPU0 00000081 00000000"
[Sat Jul 12 20:50:58 2008] notifying client 5480[111:123]
[Sat Jul 12 20:50:58 2008] notifying client 5648[0:0]
[Sat Jul 12 20:50:58 2008] completed event "processor CPU0 00000081 00000000"
[Sat Jul 12 20:50:59 2008] received event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:50:59 2008] notifying client 5480[111:123]
[Sat Jul 12 20:50:59 2008] notifying client 5648[0:0]
[Sat Jul 12 20:50:59 2008] completed event "processor CPU1 00000081 00000000"


/var/log/acpid after not suspending (crashing) on LID close:
[Sat Jul 12 20:52:50 2008] received event "button/lid LID 00000080 00000001"
[Sat Jul 12 20:52:50 2008] notifying client 5480[111:123]
[Sat Jul 12 20:52:50 2008] notifying client 5648[0:0]
[Sat Jul 12 20:52:50 2008] executing action "/etc/acpi/lid.sh"
[Sat Jul 12 20:52:50 2008] BEGIN HANDLER MESSAGES
[Sat Jul 12 20:52:50 2008] END HANDLER MESSAGES
[Sat Jul 12 20:52:50 2008] action exited with status 0
[Sat Jul 12 20:52:50 2008] completed event "button/lid LID 00000080 00000001"
[Sat Jul 12 20:54:40 2008] starting up
[Sat Jul 12 20:54:40 2008] 74 rules loaded
[Sat Jul 12 20:54:41 2008] received event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:54:41 2008] completed event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:54:42 2008] client connected from 5606[111:123]
[Sat Jul 12 20:54:42 2008] 1 client rule loaded
[Sat Jul 12 20:54:44 2008] client connected from 5768[0:0]
[Sat Jul 12 20:54:44 2008] 1 client rule loaded
[Sat Jul 12 20:54:46 2008] received event "processor CPU0 00000081 00000000"
[Sat Jul 12 20:54:46 2008] notifying client 5606[111:123]
[Sat Jul 12 20:54:46 2008] notifying client 5768[0:0]
[Sat Jul 12 20:54:46 2008] completed event "processor CPU0 00000081 00000000"
[Sat Jul 12 20:54:47 2008] received event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:54:47 2008] notifying client 5606[111:123]
[Sat Jul 12 20:54:47 2008] notifying client 5768[0:0]
[Sat Jul 12 20:54:47 2008] completed event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:54:48 2008] received event "processor CPU0 00000081 00000000"
[Sat Jul 12 20:54:48 2008] notifying client 5606[111:123]
[Sat Jul 12 20:54:48 2008] notifying client 5768[0:0]
[Sat Jul 12 20:54:48 2008] completed event "processor CPU0 00000081 00000000"
[Sat Jul 12 20:54:49 2008] received event "processor CPU0 00000081 00000000"
[Sat Jul 12 20:54:49 2008] notifying client 5606[111:123]
[Sat Jul 12 20:54:49 2008] notifying client 5768[0:0]
[Sat Jul 12 20:54:49 2008] completed event "processor CPU0 00000081 00000000"
[Sat Jul 12 20:54:50 2008] received event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:54:50 2008] notifying client 5606[111:123]
[Sat Jul 12 20:54:50 2008] notifying client 5768[0:0]
[Sat Jul 12 20:54:50 2008] completed event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:54:51 2008] received event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:54:51 2008] notifying client 5606[111:123]
[Sat Jul 12 20:54:51 2008] notifying client 5768[0:0]
[Sat Jul 12 20:54:51 2008] completed event "processor CPU1 00000081 00000000"
[Sat Jul 12 20:55:23 2008] received event "thermal_zone THRM 00000081 00000000"
[Sat Jul 12 20:55:23 2008] notifying client 5606[111:123]
[Sat Jul 12 20:55:23 2008] notifying client 5768[0:0]
[Sat Jul 12 20:55:23 2008] completed event "thermal_zone THRM 00000081 00000000"
[Sat Jul 12 20:56:08 2008] received event "thermal_zone THRM 00000081 00000000"
[Sat Jul 12 20:56:08 2008] notifying client 5606[111:123]
[Sat Jul 12 20:56:08 2008] notifying client 5768[0:0]
[Sat Jul 12 20:56:08 2008] completed event "thermal_zone THRM 00000081 00000000"
[Sat Jul 12 20:56:43 2008] received event "thermal_zone THRM 00000081 00000000"
[Sat Jul 12 20:56:43 2008] notifying client 5606[111:123]
[Sat Jul 12 20:56:43 2008] notifying client 5768[0:0]
[Sat Jul 12 20:56:43 2008] completed event "thermal_zone THRM 00000081 00000000"

---

### Post by bogoliubov on 2008-07-27
I've filed a bug report about it. So far I've got no reaction, but I guess it takes some time...

Still, if anyone knows of a solution, or something to look for, I'd be grateful.

---

### Post by bogoliubov on 2008-09-16
Hmm, I just found a thing which seems to be wrong:

In /etc/acpi/lid.sh, a support script /usr/share/acpi-support/power-funcs is being run in the beginning. 
In this supportscript (/usr/share/acpi-support/power-funcs),
there is a variable called LIDSTATE:
LIDSTATE='/var/lib/acpi-support/lidstate'

Now, if I look in /var/lib/acpi-support/ there is nothing! This seems very strange!

---

