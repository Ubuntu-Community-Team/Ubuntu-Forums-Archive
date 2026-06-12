---
title: "Unetbootin &quot;command not found&quot; error"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by 801 on 2009-06-13
Hi,

I'm trying to install Easy Peasy on my Asus netbook, following the instructions found here:
[http://wiki.geteasypeasy.com/Get_Easy_Peasy](http://wiki.geteasypeasy.com/Get_Easy_Peasy) (2ND)
and here:
[http://wiki.geteasypeasy.com/How_to:_Using_Unetbootin#Install](http://wiki.geteasypeasy.com/How_to:_Using_Unetbootin#Install)

Unetbootin is executable. However, when I click (or use the command line instructions in second link) I get the "Command not found" error message.
I did the "sudo aptitude install p7zip-full" and had it installed, but still no go. Please help?
Thank you.

---

### Post by kerry_s on 2009-06-13
**sudo apt-get install unetbootin**

---

### Post by 801 on 2009-06-13
Thanks for you quick answer.
It says "Package not found".

---

### Post by albinootje on 2009-06-13
> **801 said:**
> 
Unetbootin is executable. However, when I click (or use the command line instructions in second link) I get the "Command not found" error message.

Please do an "ls -la unet*" in the current directory of the location where your unetbootin binary is located.

And please post the output (if any) of "grep -i noexec /etc/fstab".

---

### Post by 801 on 2009-06-13
Goedenavond ;-)

ls -al unet*:
-rwxr-xr-x 1 user user 3532812 2009-06-13 23:13 unetbootin-eeeubuntu-linux-276

where "user user" has been anonymised...

and the grep command does not give any output.


However... I had an idea a few minutes ago. I downloaded the unetbook directly from the Easy Peasy (ie Sourceforge) site, bit the Easy Peasy iso image was downloaded using bittorrent. The files/iso's have different names, it appears. I'm downloading the iso image from the Easy Peasy site to see if that might help. 16 minutes remaining....

Dankjewel ;-)

---

### Post by albinootje on 2009-06-13
> **801 said:**
> Goedenavond ;-)

Hee, .. goeienavond! ;-)
> 
ls -al unet*:
-rwxr-xr-x 1 user user 3532812 2009-06-13 23:13 unetbootin-eeeubuntu-linux-276

So, the command ./unetbootin-eeeubuntu-linux-276 didn't do anything at all?

Does easypeasy need a customized unetbootin ?
If not, download it here : [http://unetbootin.sf.net](http://unetbootin.sf.net)

---

### Post by 801 on 2009-06-13
OK, thanks. It appears the click in Konqueror still seems to get a "Command not found" error, but the command line options (using ./ at the start of the line, which I forgot previously) seems to work now.
The USB light is flashing, install is working.
My problem solved, it is installing. But then there's still the question why does it not work in the Konqueror mode?
Dankjewel voor de hulp!

---

### Post by kerry_s on 2009-06-13
> **801 said:**
> Thanks for you quick answer.
It says "Package not found".

sorry, i'm using debian testing and it's in are repos, so i assumed it would be in ubuntu repos.

---

### Post by albinootje on 2009-06-13
> **801 said:**
> But then there's still the question why does it not work in the Konqueror mode?

Hmm, no idea.
> 
Dankjewel voor de hulp!
Geen probleem.

> **kerry_s said:**
> sorry, i'm using debian testing and it's in are repos, so i assumed it would be in ubuntu repos.
Unetbootin is available in Jaunty and Karmic.

---

### Post by 801 on 2009-06-13
> **kerry_s said:**
> sorry, i'm using debian testing and it's in are repos, so i assumed it would be in ubuntu repos.

No problem! Any help is appreciated, even if it doesn't work ;-).

BTW: Easy Peasy installation:

On the site it says "follow onscreen instructions". No go.
What you need to do is boot the live-disc ("default" option, not the "OEM" or "help" option). Once the live boot is running, go to "Administration" (bottom left) and choose install. After that follow the onscreen instructions.

---

