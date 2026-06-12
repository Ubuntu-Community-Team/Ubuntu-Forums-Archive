---
title: "Does Ubuntu Studio have a graphical Installer?"
date: 2008-09-20
forum: General Help
---

### Post by d3drocks on 2008-09-20
title explains it all.
please help. im going to need to tripple boot my new pc with XP vista, and ubuntu studio. i know that the Kubuntu and Ubuntu CDs have really awesome partitioning tools built into the graphical installer.
if its too hard for me, how would i put the ubuntu studio kernel in normal ubuntu?

---

### Post by ladr0n on 2008-09-20
Your best bet (and what I do) will be to install the regular ubuntu desktop CD.  Once that is finished, open synaptic and search for "Ubuntu Studio".  Check everything (that you actually want to install) for installation, and hit apply.  Once it finishes, reboot and select the real-time kernel, and you will be in a full-fledge Ubuntu Studio environment.
That way you a) don't waste a DVD, b) get a graphical installer, and c) don't necessarily install ALL of the Ubuntu Studio packages if you don't want them all.

---

### Post by PC_load_letter on 2008-09-20
IIRC, I don't think it does. Not before you check the components you want to install, one of the components that you may choose not to install (I don't know how on earth) is Ubuntu desktop!!! 
I installed Ubuntu Studio like two weeks ago on a Dell Vostro 1400 from the live dvd. Very smooth installation. Updates couldn't be smoother, restarted and then the wireless is working no more. My guess is that the driver got lost when the kernel was updated, but don't have the time to fix it.
Overall, I think it's very nice and worth the trouble.

---

### Post by OutOfReach on 2008-09-20
I'm pretty sure that Ubuntu Studio only has a text based installer.

---

### Post by d3drocks on 2008-09-20
> **ladr0n said:**
> Your best bet (and what I do) will be to install the regular ubuntu desktop CD.  Once that is finished, open synaptic and search for "Ubuntu Studio".  Check everything (that you actually want to install) for installation, and hit apply.  Once it finishes, reboot and select the real-time kernel, and you will be in a full-fledge Ubuntu Studio environment.
That way you a) don't waste a DVD, b) get a graphical installer, and c) don't necessarily install ALL of the Ubuntu Studio packages if you don't want them all.

sounds like a possible plan, thanks

---

### Post by d3drocks on 2008-09-25
> **ladr0n said:**
> Your best bet (and what I do) will be to install the regular ubuntu desktop CD.  Once that is finished, open synaptic and search for "Ubuntu Studio".  Check everything (that you actually want to install) for installation, and hit apply.  Once it finishes, reboot and select the real-time kernel, and you will be in a full-fledge Ubuntu Studio environment.
That way you a) don't waste a DVD, b) get a graphical installer, and c) don't necessarily install ALL of the Ubuntu Studio packages if you don't want them all.

just tried that. no results are found

---

### Post by snowpine on 2008-09-25
> **d3drocks said:**
> title explains it all.
please help. im going to need to tripple boot my new pc with XP vista, and ubuntu studio. i know that the Kubuntu and Ubuntu CDs have really awesome partitioning tools built into the graphical installer.
if its too hard for me, how would i put the ubuntu studio kernel in normal ubuntu?

If all you want is the kernel, 'sudo apt-get install linux-rt'.

It should appear at grub the next time you boot up.

---

### Post by snowpine on 2008-09-25
> **d3drocks said:**
> just tried that. no results are found

Try searching for 'ubuntustudio' without the space.
Which version of Ubuntu are you using? Gutsy and Hardy, it's in the main repository. Feisty or earlier, you have to add a repository:

[http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/](http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/)

---

### Post by d3drocks on 2008-09-25
> **snowpine said:**
> Try searching for 'ubuntustudio' without the space.
Which version of Ubuntu are you using? Gutsy and Hardy, it's in the main repository. Feisty or earlier, you have to add a repository:

[http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/](http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/)

I'm on 8.04 Hardy.

---

### Post by markbuntu on 2008-09-25
Just do it with Synaptic. You can see all the packages and choose the ones you want. I recently got just the Ununtustudio audio part for my amd64 hardy and it was painless, though a very big download. rt kernel and all installed without a hitch. 

A warning though. If you are using drivers you got directly from ati or nvidia the rt kernel may fail. It happened to me on my 32 bit hardy ubuntustudio. The best thing would be to remove these drivers and reinstall them after you get the rt kernel working.

---

