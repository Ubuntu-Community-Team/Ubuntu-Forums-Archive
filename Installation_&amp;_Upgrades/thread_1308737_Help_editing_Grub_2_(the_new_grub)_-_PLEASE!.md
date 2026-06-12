---
title: "Help editing Grub 2 (the new grub) - PLEASE!"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by ophysis on 2009-10-31
Hi,

In order for my laptop to boot with ubuntu I need to add a parameter (reserve=0xFFB00000,0x100000) to the boot command just before the splash bit.

The old grub was easy - just edit the menu.lst file, but now grub is all changed and can't really figure out what file to edit and where.

Anyone has some knowledge to share?

Andre

---

### Post by praveenthivari on 2009-10-31
Doing that is bit difficult I too wanted to do that but the procedure is entirely different.
It requires a bit of work. Following these links may help:

[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries](https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries)

[http://ubuntuforums.org/showthread.php?t=1308669](http://ubuntuforums.org/showthread.php?t=1308669)

---

### Post by drs305 on 2009-10-31
> **ophysis said:**
> Hi,

In order for my laptop to boot with ubuntu I need to add a parameter (reserve=0xFFB00000,0x100000) to the boot command just before the splash bit.

The old grub was easy - just edit the menu.lst file, but now grub is all changed and can't really figure out what file to edit and where.

Anyone has some knowledge to share?

Andre

If this is an option you used to put on the kernel line, like "acpi=off", you can add it to /etc/default/grub.

If it needs to appear on any boot, normal or recovery, add it to the line:
GRUB_CMDLINE_LINUX=

If it should only go on the normal boots, add it to this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 

Save the file, then run "sudo update-grub"

The Ubuntu community doc in the first link in the previous post explains what the settings in /etc/default/grub do. You can also access it by clicking on the GRUB2 link in my signature line.

---

### Post by ophysis on 2009-11-09
Tks guys,

I still can't get it to work, but your advice was exactly what I needed.

It boots now, but into a command line only... No gui. :(

It's a very specific relationship ubuntu/laptop. [[COLOR="Blue"]_This website_[/COLOR]]("www.fitzenreiter.de/averatec/index-e.htm") has been helping in the past, but now I get the above problem.

Maybe someone can help with this one.

Andre

---

### Post by drs305 on 2009-11-09
> **ophysis said:**
> Tks guys,

I still can't get it to work, but your advice was exactly what I needed.

It boots now, but into a command line only... No gui. :(



If it is booting to the Ubuntu command line then you would probably have more success opening a new thread under your own title. It would draw more readers likely to be able to help, especially with a descriptive title. Glad you can boot, hopefully you will soon be able to actually use it.  ;-)

---

### Post by blauegeist on 2009-11-09
I was wondering if in grub 2 menu entries can be commented out like in the previous one. I have a recovery partition that is shown and i would like to hide it. 
thanks 
blauegeist

---

### Post by drs305 on 2009-11-09
> **blauegeist said:**
> I was wondering if in grub 2 menu entries can be commented out like in the previous one. I have a recovery partition that is shown and i would like to hide it. 
thanks 
blauegeist

If you want to hide all the recovery partitions, you can disable their display in the /etc/default/grub file:
> GRUB_DISABLE_LINUX_RECOVERY="true"

You have to edit the file as root, and then run "sudo update-grub" after you have saved the changes.

It is possible to "Comment out" the lines but it isn't the desired method. For one, the /boot/grub/grub.cfg file is read-only, even to root. If you make it writable, any time update-grub is run or a new kernel is introduced the file will be replaced, your changes will be removed, and the file will once again be made read-only.

---

### Post by blauegeist on 2009-11-10
thanks drs305, i should have been more clear, i dual boot with windows, i meant the windows recovery.

---

### Post by drs305 on 2009-11-10
> **blauegeist said:**
> thanks drs305, i should have been more clear, i dual boot with windows, i meant the windows recovery.

One method would be to place a filter in /etc/grub.d/30_os-prober.

First you would determine the exact title Grub 2 gives to your Windows Recovery partition (the menuentry between the quotes in /boot/grub/grub.cfg).

You would then place a line in the file so that when the os-prober finds the Recovery partition, it moves on without including an entry in the menu.

If you want to try to do it yourself, refer to this post and look at Section 2:
[Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

If you give us the exact title we can probably help you modify the 30_os-prober script.

Since you aren't the OP of this thread I would recommend you respond in the linked thread if you want to try this (and include the menuentry).

---

### Post by ophysis on 2009-11-10
> **drs305 said:**
>  ... you would probably have more success opening a new thread under your own title. It would draw more readers likely to be able to help... 

Tks. Will do.

Andre

---

### Post by blauegeist on 2009-11-10
This is what my menu entry looks like for windows in grub.cfg

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 800e-1b1c
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set c6fe5a94fe5a7d1d
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

The first entry /dev/sda1 is the recovery partition.  by that I mean that it reloads windows to original state when I bought the notebook. I would like to hide it so that I don't accidentally click it.

---

### Post by oldfred on 2009-11-11
drs305 often has some good work arounds that are logic based in the  prober.

My work around is just copy your windows entry into /etc/grub.d/40_custom and turn osprober off in /etc/default/grub.
GRUB_DISABLE_OS_PROBER=true

If you modify system you can turn the prober on again to find the new settings to manually add if you want.

---

### Post by drs305 on 2009-11-11
blaugeist,

The Grub 2 Tweaks thread was closed when Karmic was officially released. I have asked that it be reinstated but will reply here.

To hide the Windows Recovery partition, try this:

Backup the existing /etc/grub.d/30_os-prober file, remove the executable bit from the backup so it isn't run during updates,  and open the original for editing:
```

sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober.original  && sudo chmod -x /etc/grub.d/30_os-prober.original
gksu gedit +83 /etc/grub.d/30_os-prober &

```

Add the highlighted entry. It looks for an entry which would be entered as "Windows Vista (loader) (on /dev/sda1)". If the menu entry or partition changes, make the same changes below:
> 
for OS in ${OSPROBED} ; do
  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
  BOOT="`echo ${OS} | cut -d ':' -f 4`"

 
  if [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi
[COLOR="DarkRed"]
[B]# Added to remove Windows Recovery
  if [ "$LONGNAME" = "Windows Vista (loader)" ] && [ "${DEVICE}" = "/dev/sda1" ] ; then
       continue
  fi
# End Added[/B][/COLOR]


Save the file, then run:
```
sudo update-grub
```

Please let me know if this does what you want. If so, I will add it to the Grub 2 Tweaks link if the mods return it to an active forum.

---

### Post by blauegeist on 2009-11-11
@drs305 I did what you said to do but it got rid of both entries. Maybe /dev/sda1 is not so important as what comes before. 
perhaps i have to rename the "windows vista (loader)" part so that they differ and then it might help

thanks blauegeist

---

### Post by drs305 on 2009-11-11
my apologies blauegeist,

I corrected part of the script to ensure that Vista on sda2 would not be hidden, even with the same Title.

I've edited the original to avoid confusion for anyone who follows this thread. Please try it again.

---

### Post by blauegeist on 2009-11-11
drs305 
for some reason it still hides both, however if i change "/dev/sda1 to /dev/sda2 then it hides the second entry

---

### Post by drs305 on 2009-11-11
> **blauegeist said:**
> drs305 
for some reason it still hides both, however if i change "/dev/sda1 to /dev/sda2 then it hides the second entry

I'm not a script expert and am not sure why it won't hide Vista sda1. If you didn't, try cut/paste to make sure there are no typos.  You can try just hiding the entry for sda1, no matter what it is (in your case the recovery partition) with this:
> if [ ${DEVICE} = "/dev/sda1" ] ; then

---

### Post by blauegeist on 2009-11-11
Thanks for your help drs305 
the last bit you gave also hid both parts. 
maybe the only to do it is to edit the config.
I hope they have something to fix this because i dont want to edit the config file, but i also dont want to have to install linux all over again because i hit the first windows entry.:(

---

### Post by drs305 on 2009-11-12
> **blauegeist said:**
> Thanks for your help drs305 
the last bit you gave also hid both parts. 
maybe the only to do it is to edit the config.
I hope they have something to fix this because i dont want to edit the config file, but i also dont want to have to install linux all over again because i hit the first windows entry.:(

I have sent you several Private Messages. Perhaps we can work this out via IM or IRC. You can access your Inbox via the "User CP" link at the top left of this page.

---

