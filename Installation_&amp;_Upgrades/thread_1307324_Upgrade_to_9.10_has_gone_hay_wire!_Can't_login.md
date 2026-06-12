---
title: "Upgrade to 9.10 has gone hay wire! Can't login"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by myromance123 on 2009-10-31
My computer is now unusable. I get that white ubuntu logo after it says starting boot up(or something similar) but then after the white logo (which does nothing) it goes back to the starting boot up !
THEN, it flickers like mad!!
 Non-stop. It then somehow heads to login screen but the type you get if you press alt-f1 (or where its like the screen is only the terminal). The problem here is because of the mad flickering I can't login ! So I can't fix it. The mad flickering causes pauses and loss of input so when I click a key on the keyboard I have to hit it several times then it will appear. I can't do this for the password since I can't see the keys I'm typing in!

Possible reasons I think this happened with my machine:
1. Nvidia Binary Drivers are installed (185.18.36 which could be the reason X crashed on start up).
2. I first attempted the upgrade through the internet but had no luck several times (where I live the internet has major issues and is slow) so the third time I tried using the alternate CD and I chose 'NO' when it asked about network, yet oddly enough it still forced me to have an internet connection throughout the upgrade or else it would say it couldn't find this or that file.
So I let the net connection stay on and I left it overnight (the CD helped me get more than halfway through what needed to be downloaded, the rest depended on the net).
I woke up today and was greeted with the restart now panel. So I did it. I clicked restart now (nothing running in the background except Cairo Dock).
Now's where the problem is. 

Is there a way for me to use GRUB to uninstall the Nvidia driver?
I don't think there is a possible other solution besides somehow using GRUB to help remedy this.

PLEASE, be easy to understand because I have never done anything GRUB related before. If its terminal wise I should be ok.

I really need help here. :(

---

### Post by myromance123 on 2009-10-31
Ok, I have managed to fix the problem on my own.

Here's what I did.
At start up normally it will say "Press 'Esc' to Enter GRUB" which I did, I pressed ESC.
Then I chose Ubuntu 9.04 recovery mode.
After which I chose the line that says "DPKG  Repair Broken Packages"
Waited a bit and then entered 'n' and pressed Enter when it asked to continue with Upgrade or not.
After that it did the usual (like what it does in the update manager). I entered 'y' to all it asked.
Then I pressed Enter when it finished.
Why I did this is because I suspected some packages to be out of sync with others due to a half network half alternate CD upgrade.
That hopefully solves that.

Now to the issues of the Nvidia Binary Driver. I ALWAYS keep a copy of the .run of it on the Desktop. So this time I chose from the menu "Resume normal boot up".

It came to the login screen (terminal one) and I entered my information no problem (oddly no flickering here).

After which I cd to Desktop and entered the folder which had my nvidia .run file. I ran it and followed the instructions as per normal.
After done with installing it I entered "sudo shutdown -h now" withouth the double quotes to completely shutdown the computer.

I started the computer back up and voila it all works now :D

The white ubuntu logo scared me cos it didn't do anything again and it went temporarily back to the screen which says "Boot up from..... Starting up"

But then it came to the splashscreen and now I am in :D

Yay!

9.10 for me hehe

 :D

---

