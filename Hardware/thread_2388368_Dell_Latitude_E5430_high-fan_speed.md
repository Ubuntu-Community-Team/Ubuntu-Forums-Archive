---
title: "Dell Latitude E5430 high-fan speed"
date: 2018-04-01
forum: Hardware
---

### Post by moto1860 on 2018-04-01
Need to apply a solution I've found on askubuntu: [https://askubuntu.com/questions/516067/persistent-high-fan-speed-ubuntu-14-04?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/516067/persistent-high-fan-speed-ubuntu-14-04?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

What do I subsititute [COLOR=#111111][FONT=Consolas]sudo gedit /etc/default/grub with  in my case to make it run?

**[SIZE=2]Tho grub is not installed on my laptop at the moment right?[/SIZE]**

[/FONT][/COLOR]```
avo@avo-Latitude-E5430-non-vPro:~$ grub-install -vgrub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
Installing for i386-pc platform.
grub-install: error: install device isn't specified.



```[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2018-04-01
> **moto1860 said:**
> 
**[SIZE=2]Tho grub is not installed on my laptop at the moment right?[/SIZE]**



If this is a single boot OS or dual boot OS grub is usually installed by default.
Open a terminal and paste this in:
```
gedit /etc/default/grub
```
paste that back or if looks anything like this:
```
# GRUB boot loader configuration

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR='SwagArch'
GRUB_CMDLINE_LINUX_DEFAULT="quiet resume=UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83$
GRUB_CMDLINE_LINUX=""

# Preload both GPT and MBR modules so that they are not missed
GRUB_PRELOAD_MODULES="part_gpt part_msdos"

# Uncomment to enable booting from LUKS encrypted devices
#GRUB_ENABLE_CRYPTODISK=y

# Uncomment to enable Hidden Menu, and optionally hide the timeout count
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=true

# Uncomment to use basic console
GRUB_TERMINAL_INPUT=console

```
Then you have grub installed.

---

### Post by moto1860 on 2018-04-01
Yes it appears to be installed. What would then be my subs for [COLOR=#111111][FONT=Consolas]gedit /etc/default/grub?[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2018-04-01
> **moto1860 said:**
> Yes it appears to be installed. What would then be my subs for [COLOR=#111111][FONT=Consolas]gedit /etc/default/grub?[/FONT][/COLOR]

It's unclear to me what you are trying to modify from that link you show has more than one suggestion offered.;)
which one do you **think** you need?

---

### Post by moto1860 on 2018-04-01
Sorry should have specified it was what question owner deemed as best answer (marked in green):

[COLOR=#111111][FONT=Ubuntu]Follow these steps to try this solution:[/FONT][/COLOR]

[LIST=1]
[*]Open a terminal, type sudo gedit /etc/default/grub, and press Enter
[*]Enter your login password and press Enter. The password will not be displayed as you type it.
[*][FONT=inherit]Edit the line[/FONT]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[FONT=inherit]such that it reads[/FONT]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=!Windows 2012"
[*][FONT=inherit]Click "Save", wait a few moments for the file to save, then close the text editor.[/FONT]
[*][FONT=inherit]In the terminal, type sudo update-grub and hit Enter[/FONT]
[*][FONT=inherit]Finally, shut down your computer. Shut it down completely: don't restart it.[/FONT]
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Once you turn your computer back on and select the linux operating system whose grub file you edited earlier, your fans should be working normally. This solution has worked for me on Ubuntu, Linux Mint, Elementary OS, and LXLE on a Dell Inspiron 15R 5520 laptop.[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2018-04-01
Alrighty then:)
First open the terminal and enter this:
```
sudo -H gedit /etc/default/grub
```
Now you have a file you can edit>>>Look for the line that looks as described by that poster:
EG:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
And add the added comment at the end so it looks like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=!Windows 2012"
```
That has to read exact spaces and quotes.
Now if you are still unsure feel free to show your edit here for us to look at>> to be sure. :)

And when all is good>> save and close the text file and 
OOpps forgot to tell grub about the change with:
```
sudo update-grub
```.
I hope your sure about this as it fits a specific model laptop. ;)

---

### Post by moto1860 on 2018-04-01
> **1fallen said:**
> Alrighty then:)
First open the terminal and enter this:
```
sudo -H gedit /etc/default/grub
```

```
avo@avo-Latitude-E5430-non-vPro:~$ sudo -H gedit /etc/default/grub
[sudo] password for avo: 
No protocol specified
Unable to init server: Could not connect: Connection refused


(gedit:9930): Gtk-WARNING **: cannot open display: :0



```

---

### Post by #&amp;thj^% on 2018-04-01
> **moto1860 said:**
> ```
avo@avo-Latitude-E5430-non-vPro:~$ sudo -H gedit /etc/default/grub
[sudo] password for avo: 
No protocol specified
Unable to init server: Could not connect: Connection refused


(gedit:9930): Gtk-WARNING **: cannot open display: :0



```
You have problems here???
Have you been using "sudo" when opening any GUI's? (such as a file manger or text editor's.)
These problems will need to be addressed sooner than later. :(
anyway see if nano works via:
```
sudo nano /etc/default/grub
```  
and follow the rest of the post I gave you in post#6
To save that file when done use the keys <ctrl+o> (That is the letter o and not the number 0 ) and quit with <ctrl+x>

---

### Post by moto1860 on 2018-04-02
> **1fallen said:**
> You have problems here???
Have you been using "sudo" when opening any GUI's? (such as a file manger or text editor's.)

Can't say I'm able to answer that....


> **1fallen said:**
> 
anyway see if nano works via:
```
sudo nano /etc/default/grub
```  
and follow the rest of the post I gave you in post#6
To save that file when done use the keys <ctrl+o> (That is the letter o and not the number 0 ) and quit with <ctrl+x>
Do I edit it in a readme-like file that is supposed to open after that command? Cause it's not showing, I get this within the terminal:

[IMG]https://image.ibb.co/f86bVS/Screenshot_from_2018_04_02_06_56_13.png[/IMG]


Earlier on when I was trying to mess up with grub commands I had a smiliar text like the one I've post here in the image but opened in a readme-like file that was easier to edit.

---

### Post by #&amp;thj^% on 2018-04-02
I'm not following your question? >>>but this is more or less a console based editor.
To navigate use your up and down arrow keys to the line "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and now arrow right to add the "acpi_osi=!Windows 2012" at the end.
BTW you can use your mouse to hightlight selected text, then a right click copy to a reply or a text file>>>much better than posting images. :)
Now when you have made the change>>>copy all that is shown from the terminal so we can have a quick peek. 
> Earlier on when I was trying to mess up with grub commands I had a smiliar text like the one I've post here in the image but opened in a readme-like file that was easier to edit. 
Still not sure, but it sounds like this could be related to your gedit problem>>>But one problem per post please, Less confusing. :) And the proper way to do things here in UF.

---

### Post by moto1860 on 2018-04-02
> **1fallen said:**
> 

And when all is good>> save and close the text file and 

It's here that I'm lost.
I've typed [COLOR=#000000][FONT=&amp]sudo -H gedit /etc/default/grub  I've now edited that specific line but how do I go on after I've edited?
At the bottom I've an option to exit it marked with ^X but not to save and close.[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2018-04-02
> **moto1860 said:**
> It's here that I'm lost, what text file? 
I've typed [COLOR=#000000][FONT=&amp]sudo -H gedit /etc/default/grub and I got what I posted as a screenshot, which looks like a text file but within the terminal, I've now edited that specific line but how do I go on after I've edited?
At the bottom I've an option to exit it marked with ^X but not to save and close.[/FONT][/COLOR]

Paste all that back here please>> the content of **"nano /etc/default/grub"**
We seem to have a big communication problem.

---

### Post by moto1860 on 2018-04-02
> **1fallen said:**
> Paste all that back here please>> the content of **"nano /etc/default/grub"**
We seem to have a big communication problem.

```


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
                   [ File '/etc/default/grub' is unwritable ]
^G Get Help  ^O Write Out ^W Where Is  ^K Cut Text  ^J Justify   ^C Cur Pos
^X Exit      ^R Read File ^\ Replace   ^U Uncut Text^T To Spell  ^_ Go To Line



```

---

### Post by #&amp;thj^% on 2018-04-02
> **moto1860 said:**
> ```


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
                   [ File '/etc/default/grub' is unwritable ]
^G Get Help  ^O Write Out ^W Where Is  ^K Cut Text  ^J Justify   ^C Cur Pos
^X Exit      ^R Read File ^\ Replace   ^U Uncut Text^T To Spell  ^_ Go To Line



```

See I'm glad we did this< I was under the impression you had made the change already, but it still shows as orignal.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Should read now as:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=!Windows 2012"
``` 
And before we go on** I still beg you to consider this fix was for a different model laptop than yours**.
That said **I bear no responsibility for any bad outcomes to your system or hardware**. ;) I hope that is now very clear! 
And maybe all will be good with this, but I feel the need to at least point this out.

---

### Post by moto1860 on 2018-04-02
I understand I've to edit that line, what's not clear to me is what to do after I've edited that line as I don't have a save option avialable under file at the top left of the terminal.

I know it's not my model I'd like to give it a shot.

---

### Post by #&amp;thj^% on 2018-04-02
> **moto1860 said:**
> I understand I've to edit that line, what's not clear to me is what to do after I've edited that line as I don't have a save option avialable under file at the top left of the terminal.

I know it's not my model I'd like to give it a shot.
Right Then, to save the file use keyboard combination of "ctrl+o" then>> enter>> then keycombo "ctrl+x"
To be clear hit the "ctrl" holding down that key and the letter "o" writes the file, Now keycombo "ctrl" holding down and the letter "x" saves and closes the file.
Now tell grub about the change with:
```
sudo update-grub
```
Reboot and I wish you the best. :)

---

### Post by moto1860 on 2018-04-02
> **1fallen said:**
> Right Then, to save the file use keyboard combination of "ctrl+o" then>> enter

I'm getting this before being able to save and close [ Error writing /etc/default/grub: Permission denied ]

```
GNU nano 2.8.6               File: /etc/default/grub                Modified  

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=!Windows 2012"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
             [ Error writing /etc/default/grub: Permission denied ]
^G Get Help  ^O Write Out ^W Where Is  ^K Cut Text  ^J Justify   ^C Cur Pos
^X Exit      ^R Read File ^\ Replace   ^U Uncut Text^T To Spell  ^_ Go To Line



```

---

### Post by #&amp;thj^% on 2018-04-02
Then you did not follow my instructions..:)
To edit you need as i said:
```
sudo nano /etc/default/grub
```
This allows the permissions needed to read and write.
where as "nano /etc/default/grub" is a read only permission no changes are permitted.
In the future please read all said in a post/thread very carefully with full understanding, it will save you much frustration and heartache. (I mean this in the nicest way possible )

---

### Post by deadflowr on 2018-04-02
Is sudo not working right?
Or are you running the command nano /etc/default/grub without sudo.
Note that only an admin will have the proper rights to run sudo commands.

---

### Post by moto1860 on 2018-04-02
My bad, sorry. I've now edited and saved properly. Will update in a few minutes on whether this has worked out but I can already tell you that after reboot fan is not in high speed mode as it was before so thanks *1fallen*

---

### Post by #&amp;thj^% on 2018-04-02
Your Welcome my friend.:)
Hope that works out as you had hoped!
I'll check back to see your findings.
Kind Regards

---

### Post by moto1860 on 2018-04-02
Well, this had definitely worked out well, not sign of high speed at all. Thanks a lot :D

---

