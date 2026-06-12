---
title: "Screen resolution keeps changing itself.  That is bad."
date: 2011-07-30
forum: Hardware
---

### Post by joshgura on 2011-07-30
home theater set up, awesome.

i go into the ati catalyst settings and make the resolution just right, oh yeah.

i turn on the computer or wake it up from sleep mode -- um....

all of a sudden the resolution is wrong.  this is a bummer.

when i go into adminstration mode and tell ubuntu to be one resolution and it just decides to change itself and do its own thing, that is just bad, this means its broken as far as i am concerned. 

i researched this and i find that everyone in the world has the same problem.

does Ubuntu have any idea how to go about correcting this?

---

### Post by vlbaindoor on 2011-07-30
> **joshgura said:**
> home theater set up, awesome.

i go into the ati catalyst settings and make the resolution just right, oh yeah.

i turn on the computer or wake it up from sleep mode -- um....

all of a sudden the resolution is wrong.  this is a bummer.

when i go into adminstration mode and tell ubuntu to be one resolution and it just decides to change itself and do its own thing, that is just bad, this means its broken as far as i am concerned. 


A bit more details about your hardware itself would be useful there.

When you run the ATI Catalyst Settings and then again as you say it 'go into administration mode' - are you doing these as a Sudo user or as a normal user?

I have a Nvidia card and to run the Nvidia X Server Settings I normally go into a terminal shell under Gnome and go into 'Sudo' mode by doing 'sudo bash', key in my password and then run 'nvidia-settings' - as you may know this would run the nvidia-settings as an administrator and would actually modify the required system files. Sadly this is a GUI application but not well integrated into the Sudo mode etc under Ubuntu - so only way to get it to work correctly is to run it from a Bash shell under Gnome but with Sudo rights.

If I simply go into the 'Administration' menu on the Gnome screen, it does show up the 'Nvidia X Server Settings' option - but if I simply click it the application actually fails to write to the required files because in this case the nvidia-settings would be running without admin rights and the application is written by assuming admin rights and it does not check it.

Your hardware seems to be ATI - so you would have similar problems I guess.

---

