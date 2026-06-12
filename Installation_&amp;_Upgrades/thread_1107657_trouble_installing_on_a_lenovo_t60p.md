---
title: "trouble installing on a lenovo t60p"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by zeefreak on 2009-03-27
i'm revisiting ubuntu after a little hiatus, and i have to admit, i'm having a terrible time. i'm installing on a lenovo t60p. first, the installer kept freezing. i figured out that i had to disable acpi before it would actually install. during the install, i had no mouse, so had to do the install via keyboard only. once the machine booted, it hooked up to my wireless network, complained that my battery might be under recall, opened firefox to the battery recall page, and shortly thereafter froze. hard lockup, i had to reboot by forcing a power down.

i restart the computer, and - it won't boot anymore. it keeps freezing. so i load the recovery kernel, and i see that the whole thing grinds to a halt at 'input: ThinkPad Extra Buttons as /devices/virtual/input/input9' oddly, just before that are numerous lines about registering a bunch of acpi stuff. [i thought acpi was disabled . . .]

needless to say, i'm at a point where i seem to have no option but to attempt to reinstall, even though i just did that, and there is no guarantee that i won't be in the same situation in another 30 minutes.

anyone have any insight as to why i'm having these problems?

---

### Post by tommcd on 2009-03-27
What version of Ubuntu are you installing? Is it 8.04 or 8.10 or something else? Are you installing 32 bit or 64 bit Ubuntu?
A quick google search reveals that your laptop is quite linux friendly, as is typical for Lenovo. There is even a page on ThinkWiki about your laptop and Ubuntu:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60)
(I'm not sure if the T60 is the same configuration as your T60p). 
Also, the T60p is listed on the Ubuntu wiki hardware site:
[https://wiki.ubuntu.com/LaptopTestingTeam/LenovoT60p-2007-8dg](https://wiki.ubuntu.com/LaptopTestingTeam/LenovoT60p-2007-8dg)
I have not found any reports of the problems you are having with Ubuntu on the T60p.

Suggestion:
Download and install the Ubuntu 8.10 32 bit alternate install CD. This will provide the most fail safe install. It is a text based installer, but it is pretty easy to follow. 
Did you check the CD for defects? If you are burning from Windows, try using Iso Recorder or Infra Recorder, and burn at the slowest possible speed. Check the CD for defects from the boot up menu before you install:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And welcome to the Ubuntu forums!

---

### Post by zeefreak on 2009-03-27
version is 8.10 32bit. [i thought i had put that in my initial post.] afaik, this hardware doesn't support 64 bit os. i did run the cd check before installing the first time. 

i reinstalled, again having to disable acpi to make the installer not lock up. ubuntu installed, again, with the mouse being broken. this time however, i can't even get it to boot the first time. it just freezes every time. here is the really wierd thing: every time it freezes on boot, it freezes in a different place. sometimes in the first 1/4, sometimes it gets 1/2, sometimes further. i don't get why it isn't at least consistent.

its funny, google searches always say lenovo laptops are linux friendly - having been a lenovo and a linux/unix person for years, i can tell you, they aren't.

heh. i just rebooted again, and it came up with the logon screen. go figure. i'm going to see if i can install updates before it freezes again . . .

---

### Post by tommcd on 2009-03-28
Here are some suggestions I just thought of:
When booting the Ubuntu CD, hit F6 to add other boot options. Try these boot options, one at a time:
```

acpi_osi="Linux" 
acpi=force 
acpi=force pci=noacpi

```
That last one may need double quotes around the whole thing.

---

### Post by zeefreak on 2009-03-29
aha! i actually figured it out. this particular laptop i have 2 batteries, both of which are completely kaput. they won't hold a charge *at all*. when i run the laptop without a battery, everything works fine.

---

