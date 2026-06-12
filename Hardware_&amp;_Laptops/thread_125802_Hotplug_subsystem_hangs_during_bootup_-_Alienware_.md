---
title: "Hotplug subsystem hangs during bootup - Alienware Laptop"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by vrode on 2006-02-04
Hi,

I just received my Alienware Area51- m5700 laptop (see below url for specifics). Running ubuntu live or via install cd locks up during bootup check at the following point,

* Starting HOTPLUG subsystem 

cursor sits there with no response. 

What's "hotplug subsystem" and how can I bypass this error in order to proceed w/ bootup so I can troubleshoot this error?

Interestingly booting w/ a live knoppix cd works without a glitch.

Can anyone shed any light on this perplexing issue?

TIA,


regards,
/virendra

[http://www.alienware.com/product_detail_pages/Area-51_m5700/area-51m_features.aspx?SysCode=PC-LT-AREA51-M-5700&SubCode=SKU-DEFAULT](http://www.alienware.com/product_detail_pages/Area-51_m5700/area-51m_features.aspx?SysCode=PC-LT-AREA51-M-5700&SubCode=SKU-DEFAULT)

---

### Post by Mustard on 2006-02-04
From my limited experience with this problem, I've seen a couple of solutions kicking around.  I've heard that disabling USB legacy devices and/or onboard sound in BIOS are possible solutions to get past this problem.

I just did a search on the forum using the keywords 'hotplug subsystem hang', and I get a ton of hits, so feel free to do your own research on this.  Its a fairly common problem, and there may be more definite solutions out there.

-edit-

Another solution I just read about for the install CD is to start the install cd with acpi set to off, in the special parameters.

I think the problem is that the hotplug subsystems is loading up all the modules so any one of the modules could be the causing the issue, thus from one system to another the solution may be different.

---

### Post by vrode on 2006-02-04
This a brand new system which comes with built-in usb ports. I'll need to check bios settings for sound as you indicated and get back.

Yeah I did see number of search hits myself with various suggestions except I can't get passed the hotplug message in order for me to troubleshooting.


regards,
/virendra

---

### Post by vrode on 2006-02-04
oops, sorry about the typos :(



/regards,
/virendra

---

### Post by slavik on 2006-02-05
I get the same issue and knoppix also boots ...

the reason for it is that there is some request sent to the 'chip' (that the structure) and the responce is not received within a timeout limit.

technically, the system doesn't hang or sit, it just runs in a loop that doesn't terminate (not infinite).

if you boot into recovery mode, you will get a message spam in the following format:
[#######.######] azx_get_response timeout

# is any digit between 0 and 9 inclusively.

---

### Post by vrode on 2006-02-05
yeah I tried different boot options with no avail. see below:

live pci=noacpi  (disable acpi for pci maps)
live noapic nolapic

Anything else I can try to bypass this message? I even tried ctrl+c with no luck :(


regards,
/virendra

---

### Post by vrode on 2006-02-05
[QUOTE=slavik]I get the same issue and knoppix also boots ...

the reason for it is that there is some request sent to the 'chip' (that the structure) and the responce is not received within a timeout limit.

technically, the system doesn't hang or sit, it just runs in a loop that doesn't terminate (not infinite).

if you boot into recovery mode, you will get a message spam in the following format:
[#######.######] azx_get_response timeout

# is any digit between 0 and 9 inclusively.[/QUOTE]

-----
I've tried everything possible (i think) but I can't seem to bypass hotplug subsystem message :(

Is there anything else I can try?


regards,
/virendra

---

### Post by Mustard on 2006-02-05
All I can add is that I spent some time mucking around in BIOS with all types of options before I got around the problem.  For me it was a case of the system working well for me, then the problems started occuring after I mucked around with some BIOS settings relating to suspend or acpi (sp?), there were different modes and only one mode would work for me.  I didn't have much idea what the BIOS settings were for or what I was doing by changing them, and it was a purely hit and miss affair due to lack of knowledge on what these BIOS settings actually controlled.

---

### Post by vrode on 2006-02-05
[QUOTE=Mustard]All I can add is that I spent some time mucking around in BIOS with all types of options before I got around the problem.  For me it was a case of the system working well for me, then the problems started occuring after I mucked around with some BIOS settings relating to suspend or acpi (sp?), there were different modes and only one mode would work for me.  I didn't have much idea what the BIOS settings were for or what I was doing by changing them, and it was a purely hit and miss affair due to lack of knowledge on what these BIOS settings actually controlled.[/QUOTE]

-----------
I've tried disabling "LCD panel power saving" under my BIOS with no luck:(

If I press ALT+SysRq+E, it bypasses hotplug subsystem option but I get call trace dump :(

I'm hoping one of the ubuntu developers can jump in and help.

regards,
/virendra

---

### Post by vrode on 2006-02-05
When I booted into the system via recovery mode, hitting esc on the grub menu,

I see the following message and the cursor sits there,

snd-hda-intel: can't be laoded
missing kernel or user driver snd-hda-intel
shpchp: already loaded
uhci-hcd: already loaded
uhci-hcd: already loaded
uhci-hcd: already loaded
uhci-hcd: already loaded
<3>hw_random: RNG not detected
hw_random: can't be loaded
missing kernel or user mode driver hw_random

Back to my original question, how do I bypass this message so I can fix it?

please advice.

regards,
/virendra

---

### Post by slavik on 2006-02-05
there is a kernel boot option to disable the loading of the corresponding alsa driver module ...

---

### Post by vrode on 2006-02-07
can you list the command, please.




regards,
/virendra

---

### Post by toorima on 2006-02-07
my laptop won't boot properly if i dont enable thorough check in bios, try it

---

### Post by jannol on 2006-02-07
bootup in recovery mode and when logged in as root type

nano /etc/hotplug/blacklist

put

snd-hda-intel

on its own line, press ctrl+x and choose yes to save, then reboot to test if it helps, if it does there is some issue loading sound driver, there might be some patch or fix for this but I havn't tried any of them myself.

btw, this is not a solution since it disables sound. It is just to test if thats the prob.

---

### Post by slavik on 2006-02-07
well, I tried blacklisting lots of things (in dapper) still nothing ... I am thinking that it ahs something to do with the compiled kernel, since only ubuntu so far is doing this. knoppix doesn't (it actually loads the proper sound driver).

---

### Post by slavik on 2006-02-07
during boot, add the following to the kernel line:
hda-intel:enable=0

I think that should work.

---

### Post by Wouterrr on 2006-02-08
Hi 

for me its the first time im gonna use a linux on my pc but i had the same problems on my Asus A6Qva. The problem with my laptop was the soundcard.
When i disabled it in the bios the problem was solved.
So maybe you can try to disable it in your bios and try to reboot again.

But the next problem i have is when ubuntu is ready, i have to login, but i have a black screen and cant do anything. When i push the power button is can see that i have to login, but the system is shuttingdown, so after a few sec the laptop will be powered of :cry: 
Someone has a idee how to solve the problem?

---

### Post by Wouterrr on 2006-02-08
Hmmm that last problem is also solved. The problem was the ATI driver
I downloaded the lasted driver from the ATI website, installed it and its working.

---

### Post by vrode on 2006-02-08
[QUOTE=jannol]bootup in recovery mode and when logged in as root type

nano /etc/hotplug/blacklist

put

snd-hda-intel

on its own line, press ctrl+x and choose yes to save, then reboot to test if it helps, if it does there is some issue loading sound driver, there might be some patch or fix for this but I havn't tried any of them myself.

btw, this is not a solution since it disables sound. It is just to test if thats the prob.[/QUOTE]

-------
I'm guessing using the following command is the same thing

$ chmod -x /etc/init.d/hotplug
$ reboot

Either way I guess PCMCIA (wi-fi) won't work, correct?


regards,
/virendra

---

### Post by jannol on 2006-02-08
[QUOTE=vrode]-------
I'm guessing using the following command is the same thing

$ chmod -x /etc/init.d/hotplug
$ reboot
[/QUOTE]

No it is not, that command prevents loading hotplug by turning off its exec permission and by that nothing handled by hotplug will load .

[QUOTE=vrode]-------
Either way I guess PCMCIA (wi-fi) won't work, correct?
[/QUOTE]

That is correct if you use that chmod -x /etc/init.d/hotplug command.

---

### Post by bailout on 2006-02-08
I have the same problem since I installed a usb wireless adapter via ndiswrapper. For me I just have to unplug the adapter and the boot process continues.

---

### Post by Bresenham on 2006-02-11
Hi there. I'm having the same problem with hda-intel, in an ASUS A6Vc.

[QUOTE=slavik]during boot, add the following to the kernel line:
hda-intel:enable=0

I think that should work.[/QUOTE]

I tried that, by editing the kernel commando in Grub and didn't work.

[QUOTE=jannol]bootup in recovery mode and when logged in as root type

nano /etc/hotplug/blacklist

put

snd-hda-intel

on its own line, press ctrl+x and choose yes to save, then reboot to test if it helps, if it does there is some issue loading sound driver, there might be some patch or fix for this but I havn't tried any of them myself.

btw, this is not a solution since it disables sound. It is just to test if thats the prob.[/QUOTE]

The thing is I cannot even boot up in recovery mode. In fact, i tried editing the kernel command in the recovery mode.

So, what can I do?

Thanks for the help!

---

### Post by Bresenham on 2006-02-11
Ok, now I can boot, I disabled the sound card on BIOS.
I tried to compile alsa drivers but when I do './configure' it sends this: 
"The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux)."

I have just installed the linux-686 kernel using apt-get, so it may be related to that. Now, where can I find this directory with the kernel sources?

Thanks!

---

### Post by Bresenham on 2006-02-11
Well, now I've done 'sudo apt-get install linux-source-2.6.12', got the source code but still that one file, version.h, is not there! It seems to be the only freaking file missing...
Any help?

---

### Post by Mustard on 2006-02-11
[QUOTE=Bresenham]Well, now I've done 'sudo apt-get install linux-source-2.6.12', got the source code but still that one file, version.h, is not there! It seems to be the only freaking file missing...
Any help?[/QUOTE]

If I recall correctly, there is a linux-source package specific to the 686 kernel.

---

### Post by elappala on 2006-02-23
I have had this problem on an old Dell Latitude CPTc I have converted to a Linux box.  The sometimes the old turn it off and do a cold boot worked for a while. Removing the wireless NIC during boot then inserting it after bootup is complete seems to solve the problem
Eric

---

### Post by SteveHoffmanUK on 2006-03-06
Have just installed ubuntu on my Dell Latitude and ran into the problem of hanging on Hotplug install during bootup.

The Latitude has an external floppy drive that plugs into a special socket (not USB), and I discovered that by not having the floppy plugged in during bootup it no longer hangs.

That gets me up and running, but, of course, it means that I don't have a floppy available, and since my laptop has only a CD read-only drive, I've got no way of transferring data out of my laptop -- networking is some way down the line :-? 

This probably doesn't help Vrode, but I thought I'd contribute what I could to the discussion.

On edit: Further experimentation (boy, is this a steep learning curve!) resulted in my being able to plug the floppy drive in **after** booting and being able to mount the drive and read/write from/to it, so I have got around the problem. :)

---

