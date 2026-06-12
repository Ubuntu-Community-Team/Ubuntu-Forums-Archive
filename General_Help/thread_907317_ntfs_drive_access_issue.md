---
title: "ntfs drive access issue"
date: 2008-09-01
forum: General Help
---

### Post by squall321 on 2008-09-01
it seems weird really but my XP drive apparently is in use...but im nto using it.. im on my ubuntu install and i cant mount it because it is being used.. but used by what exactly ?

Anyone ever got that ?

here is the terminal stuff:

```
squall@Squall-desk:~$ sudo mkdir /media/windows
squall@Squall-desk:~$ sudo mount -t ntfs /dev/sda1 /media/windows
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/windows ntfs-3g force 0 0
```

i dont want to force it if its going to damage it in anyway cause all my backups are there..

EDIT:: sorry guys seems i fixed it. the power cut out the otehr day while i was booting xp and thats why i got the "$LogFile indicates unclean shutdown (0, 0)". so i booted it up again as normal and restarted and walla..

---

### Post by coffeecat on 2008-09-01
Is this your Windows C: partition?

> ```
$LogFile indicates unclean shutdown (0, 0)
```Did you have an unclean shutdown last time you were in Windows? If so, boot into Windows. If there is a problem with the journal, Windows will probably take longer to boot up as it corrects any errors, but once you are in Windows, try a 'chkdsk' anyway and then reboot into Ubuntu and see what you get.

**Edit:** You posted your edit at the same time as I posted. :)
> **squall321 said:**
> 
EDIT:: sorry guys seems i fixed it. the power cut out the otehr day while i was booting xp and thats why i got the "$LogFile indicates unclean shutdown (0, 0)". so i booted it up again as normal and restarted and walla..

Now, how did I know that? :lol:

---

