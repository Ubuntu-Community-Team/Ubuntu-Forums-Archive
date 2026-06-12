---
title: "Suspend/resume broken on ThinkPad X32 [SOLVED]"
date: 2011-01-14
forum: Hardware
---

### Post by runbei on 2011-01-14
My ThinkPad X32 did not shut off the backlight when I suspended it. It also didn't resume properly. Shutdown worked normally.

Althought I use Linux Mint, I am posting the solution here because it is a well-known issue in Debian, Mint, Ubuntu, Fedora, and OpenSuse. It is a problem not just with the X32 but with other laptops.

Tried various solutions (adjusting quirks settings, etc.), but nothing worked. As I searched I find that suspend/resume had caused some users to experience very serious problems on certain laptops, including disabling the startup button, thus preventing the machine from starting *at all*. 

The solutions on Launchpad pinpoint HAL settings, and the fixes do work for some users, but not all of us.

In search of a distro that would handle suspend/resume correctly, I first tried Scientific Linux. Suspend/resume worked flawlessly, but I was not happy with the package manager in SL, which leaves it to the user to resolve dependency issues that are automatically handled by Synaptic in Mint and Yast in OpenSuse.

I next tried OpenSuse 11.3 Gnome. OpenSuse had the same problem - the backlight remained on at suspend, and resume didn't work at all. 

I solved this issue by making a simple change in a start-up file in OpenSuse. I'm hoping that the solution will work in Ubuntu/Debian/Mint as well. I would therefore be grateful if someone could respond with the steps for Ubuntu/Mint/Debian that correspond to the following solution that worked in OpenSuse. 

This is an extremely vexing problem for many laptop users, with "solutions" offered that are incomplete, complex, and downright incomprehensible. So your help as "translator" would be deeply appreciated.

The solution:

1. With OpenSuse: open a terminal and type gnomesu gedit /etc/grub/menu.lst. In Mint, the command would be sudo gedit followed by the file location which I do not know. 

2. Gedit opens with the menu.lst file displayed. Down the page a bit, you'll see several sections that begin with "###Don't change this comment" 

3. The first section gives details for the default boot operating system. Somewhere in this long spec, you'll find "vga=0x314" or vga=(something different for your system). 

4. Just before or after this part, type "nomodeset" separated from the vga spec by a space.

5. Save the file and reboot. In OpenSuse, suspend/resume now works normally.

Again, I would appreciate it if someone could let future readers know where the menu.lst file is located under Linux Mint. In the past, I've found it frustrating to try to edit the menu spec with Mint 10 versions, which use Grub2. So any guidance would help greatly.

---

### Post by anotherlonegunman on 2011-03-12
with Grub2 you need to edit /etc/default/grub 
You would add nomodeset to this line: GRUB_CMDLINE_LINUX=""
Then run "sudo update-grub" in the terminal to rebuild the menu

You may run into problems with nomodeset and recent xorg servers, it wont run without KMS.

---

### Post by sirweldsalot on 2012-03-13
hi folks.
i know this is a very old thread (i found it while trying to fix my old x-32), but its still relevant.
the "nomodeset" trick has been around for a while and i have used it many times because ubuntu has never suspended correctly on this machine since 9.10. obviously something to do with the graphics driver.
this does work but (and i don't mean to offend) it seems to be more of a band-aid than a fix because, from what i see, it disables graphics in order to pull back from suspend, right?
this means you are really operating in safe mode(?) and it still takes forever to resume.
from what i can see (and i'm a noob so...), there was never a working linux graphics driver for this machine (at least after 9.10).
just my 2 cents.

---

