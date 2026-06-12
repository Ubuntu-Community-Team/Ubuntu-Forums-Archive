---
title: "Keyboard On Samsung Laptop Suddenly Mapped Incorrectly"
date: 2023-03-20
forum: Hardware
---

### Post by ImTroyMiller on 2023-03-20
My battery ran out on my Samsung laptop and after charging and restarting, the keyboard has become mapped incorrectly not only once Ubuntu has started but even on the GRUB menu.

Keyboard settings are set to "English(US)" and I've tried changing and then changing back.

I can use an wired USB keyboard and it seems to work just fine.

I see no option in BIOS settings for changing the keyboard input.

I did however find a nine year old thread on Reddit where someone else using a Samsung laptop had the exact same issue but there wasn't a resolution.

[https://www.reddit.com/r/techsupport/comments/2dnkss/samsung_laptop_keyboard_is_mapped_wrong/](https://www.reddit.com/r/techsupport/comments/2dnkss/samsung_laptop_keyboard_is_mapped_wrong/)

"A comes out as `
C comes out as a
D comes out as w"

Exactly the same output that I am getting.  I however didn't take apart my laptop and it doesn't have any damage.  Wasn't dropped or even lifted off the table when this happened.

Replies suggest " reseating the data cable" but I'm not sure what that means.  Is that just disconnecting the keyboard wire and reconnecting?

---

### Post by #&amp;thj^% on 2023-03-20
Try this please, open a terminal and run:
```
 sudo dpkg-reconfigure keyboard-configuration
```
I assume you want the  "English(US)" layout, is this correct?
```
Package configuration

         &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring keyboard-configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
         &#9474; Please select the model of the keyboard of this machine.  &#9474; 
         &#9474;                                                           &#9474; 
         &#9474; Keyboard model:                                           &#9474; 
         &#9474;                                                           &#9474; 
         &#9474;     eMachines m6800 laptop                             &#8593;  &#9474; 
         &#9474;     Ennyah DKB-1008                                    &#9618;  &#9474; 
         &#9474;     Everex STEPnote                                    &#9618;  &#9474; 
         &#9474;     FL90                                               &#9646;  &#9474; 
         &#9474;     Fujitsu-Siemens Amilo laptop                       &#9618;  &#9474; 
         &#9474;     Generic 101-key PC                                 &#9618;  &#9474; 
         &#9474;     Generic 102-key PC                                 &#9618;  &#9474; 
         &#9474;     Generic 104-key PC                                 &#9618;  &#9474; 
         &#9474;     Generic 104-key PC with L-shaped Enter key         &#9618;  &#9474; 
         &#9474;     Generic 105-key PC                                 &#8595;  &#9474; 
         &#9474;                                                           &#9474; 
         &#9474;                                                           &#9474; 
         &#9474;              <Ok>                  <Cancel>               &#9474; 
         &#9474;                                                           &#9474; 
         &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 

```
If so use the option>>"Generic 105-key PC" use the tab key and select the keyboard you need there.
Once complete you can add a compose key, but this is optional. Hit Enter to exit the GUI.

---

### Post by ImTroyMiller on 2023-03-21
> **1fallen said:**
> Try this please, open a terminal and run:
```
 sudo dpkg-reconfigure keyboard-configuration
```
I assume you want the  "English(US)" layout, is this correct?
```
Package configuration

         &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring keyboard-configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
         &#9474; Please select the model of the keyboard of this machine.  &#9474; 
         &#9474;                                                           &#9474; 
         &#9474; Keyboard model:                                           &#9474; 
         &#9474;                                                           &#9474; 
         &#9474;     eMachines m6800 laptop                             &#8593;  &#9474; 
         &#9474;     Ennyah DKB-1008                                    &#9618;  &#9474; 
         &#9474;     Everex STEPnote                                    &#9618;  &#9474; 
         &#9474;     FL90                                               &#9646;  &#9474; 
         &#9474;     Fujitsu-Siemens Amilo laptop                       &#9618;  &#9474; 
         &#9474;     Generic 101-key PC                                 &#9618;  &#9474; 
         &#9474;     Generic 102-key PC                                 &#9618;  &#9474; 
         &#9474;     Generic 104-key PC                                 &#9618;  &#9474; 
         &#9474;     Generic 104-key PC with L-shaped Enter key         &#9618;  &#9474; 
         &#9474;     Generic 105-key PC                                 &#8595;  &#9474; 
         &#9474;                                                           &#9474; 
         &#9474;                                                           &#9474; 
         &#9474;              <Ok>                  <Cancel>               &#9474; 
         &#9474;                                                           &#9474; 
         &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 

```
If so use the option>>"Generic 105-key PC" use the tab key and select the keyboard you need there.
Once complete you can add a compose key, but this is optional. Hit Enter to exit the GUI.

The command did not work.

"dpkg-query: package '[COLOR=#000000][FONT=&quot]keyboard-configuration[/FONT][/COLOR]' is not installed and no information is available"

---

### Post by #&amp;thj^% on 2023-03-21
> **ImTroyMiller said:**
> The command did not work.
Why??, your reply *did not work* is not helping here, show the terminal return, please!
> **ImTroyMiller said:**
> 
"dpkg-query: package '[COLOR=#000000][FONT=&quot]keyboard-configuration[/FONT][/COLOR]' is not installed and no information is available"
This sounds bad, anyway: [https://manpages.ubuntu.com/manpages/xenial/en/man1/dpkg-query.1.html](https://manpages.ubuntu.com/manpages/xenial/en/man1/dpkg-query.1.html)
Check for sure if this is installed still:
```
apt policy language-pack-en
language-pack-en:
  Installed: 1:22.04+20230209
  Candidate: 1:22.04+20230209
  Version table:
 *** 1:22.04+20230209 500
        500 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:22.04+20220415 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy/main i386 Packages

```

---

### Post by #&amp;thj^% on 2023-03-23
Outside of going to Samsung for support (Seems this happens a bit) please check in " etc/default/keyboard"
Mine:
```
# KEYBOARD CONFIGURATION FILE

# Consult the keyboard(5) manual page.

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

BACKSPACE="guess"
```

---

### Post by Autodave on 2023-03-24
IF this laptop has an easily removable battery, shut it down and remove battery.  Leave out for 10 minutes.  Reinstall it and try.

Are you using any USB hubs?  If so, disconnect all of them, reboot, and see is that helps.

---

### Post by ImTroyMiller on 2023-03-26
> **1fallen said:**
> Why??, your reply *did not work* is not helping here, show the terminal return, please!

I do apologize.  I actually must have mistyped the command.  I tried again by copying it and got the following output.

```

u@c:~$ sudo dpkg-reconfigure keyboard-configuration
[sudo] password for user: 
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.140ubuntu13.1) ...
update-initramfs: Generating /boot/initrd.img-5.19.0-35-generic
W: Possible missing firmware /lib/firmware/amdgpu/ip_discovery.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega10_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/aldebaran_cap.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_imu.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_0_toc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sdma_6_0_1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi10_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_mes1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/gc_11_0_1_mes.bin for module amdgpu
I: The initramfs will attempt to resume from /dev/dm-2
I: (/dev/mapper/vgubuntu-swap_1)
I: Set the RESUME variable to override this.

```

It took me through the prompts like you said and everything was already selected correctly.  I rebooted afterwords and it's still mapped incorrectly.

Those warnings seem to point to firmware missing.

---

### Post by ImTroyMiller on 2023-03-26
> **1fallen said:**
> Outside of going to Samsung for support (Seems this happens a bit) please check in " etc/default/keyboard"
Mine:
```
# KEYBOARD CONFIGURATION FILE

# Consult the keyboard(5) manual page.

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

BACKSPACE="guess"
```

Mine is the same.

---

### Post by ImTroyMiller on 2023-03-26
> **Autodave said:**
> IF this laptop has an easily removable battery, shut it down and remove battery. Leave out for 10 minutes. Reinstall it and try.

Are you using any USB hubs? If so, disconnect all of them, reboot, and see is that helps.

I'll try this as well as disconnecting and reconnecting the laptop cable...

---

### Post by #&amp;thj^% on 2023-03-28
lets try another approach, fwupd is an open source daemon that handles firmware upgrades in Linux,  to use it run:
NOTE: Since LVFS depends upon hardware vendors, it&#8217;s a good idea to check if your system manufacturer supports this feature or not.
```
sudo apt update && sudo apt upgrade -y
```
to be sure all upgrades are in place.
next:
```
sudo service fwupd start
```
the above should be already running.
now:
```
sudo fwupdmgr refresh
```
you should see some output here.
Now run the firmware update:
```
sudo fwupdmgr update
```
That should handle the firmware update in Ubuntu.
Good Luck, BTW have you tried with a Live-installer to see if the keyboard works as expected?

---

### Post by ImTroyMiller on 2023-04-01
> **1fallen said:**
> lets try another approach, fwupd is an open source daemon that handles firmware upgrades in Linux,  to use it run:
NOTE: Since LVFS depends upon hardware vendors, it&#8217;s a good idea to check if your system manufacturer supports this feature or not.
```
sudo apt update && sudo apt upgrade -y
```
to be sure all upgrades are in place.
next:
```
sudo service fwupd start
```
the above should be already running.
now:
```
sudo fwupdmgr refresh
```
you should see some output here.
Now run the firmware update:
```
sudo fwupdmgr update
```
That should handle the firmware update in Ubuntu.
Good Luck, BTW have you tried with a Live-installer to see if the keyboard works as expected?

I haven't done this yet.  I logged into Windows OS(which is on the SSD) for the first time on this laptop(which I've had for years) and it has the same issue.  I looked at the language settings and it was set correctly.

I'm thinking it may be a hardware issue or something.  I haven't added anything onto it and didn't take it apart when this happened.  The battery ran dead, I charged it, rebooted, and this error came about.

On a security related questions, could this be some type of key logging attack?

Edit: I just noticed that the Shift key works.  Holding it will capitalize letters.

---

### Post by #&amp;thj^% on 2023-04-01
> **ImTroyMiller said:**
> I haven't done this yet.  I logged into Windows OS(which is on the SSD) for the first time on this laptop(which I've had for years) and it has the same issue.  I looked at the language settings and it was set correctly.
I have a friend at Samsung, no names here, but he had told me this is not a rare occurrence mostly those 6yrs old and older.
> **ImTroyMiller said:**
> 
I'm thinking it may be a hardware issue or something.  I haven't added anything onto it and didn't take it apart when this happened.  The battery ran dead, I charged it, rebooted, and this error came about.
I'm pretty sure it's hardware.
> **ImTroyMiller said:**
> 
On a security related questions, could this be some type of key logging attack?
97% certain it's not, A very slim chance of that.

> **ImTroyMiller said:**
> 
Edit: I just noticed that the Shift key works.  Holding it will capitalize letters.
I would take it to a reputable shop and have it checked for hardware problems.
Sorry to hear all this though....
EDIT: FYI now I know you have a windows install, try going to the MS-store>>search for samsung settings download it let run.
I suppose you could weed through all the unwanted apps, Like McCaffe AV

---

### Post by ImTroyMiller on 2023-04-16
Somehow this issue was resolved.  The battery ran out and when I turn on the laptop, the keyboard worked correctly.  However the battery will now not charge and the charging button flashes red then green.

---

