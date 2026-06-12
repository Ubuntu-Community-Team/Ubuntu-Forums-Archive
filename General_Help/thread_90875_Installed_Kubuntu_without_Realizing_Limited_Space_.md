---
title: "Installed Kubuntu without Realizing Limited Space (Solved)"
date: 2005-11-16
forum: General Help
---

### Post by KevRus on 2005-11-16
I tried installing Kubuntu and here's what happened.

After installing,
I hit CTRL-ALT-Backspace to restart xserver which now that I think about it, I probably shouldn't have done, because this just re-opened Gnome.  I tried logging in Gnome, and I got an error saying I couldn't log in because I either couldn't access the home folder or there is no more room on the partition.

I assumed KDE caused this, so I reverted what I just did and sudo apt-get remove'd everything I downloaded.

This didn't help, and now when I reboot completely I get the KDE welcome screen but nothing happens when I log in.  It disappears for a second, then the log in screen pops up again, no error messages or anything.

Looking back, the error I got while logging into Gnome (Thinking it was KDE) might have just been because it was now programmed to run KDE, and I hadn't rebooted, but I don't know I'm really confused now and I can't get either desktop environment to work.  Maybe this isn't even related to my having limited space on the drive. :P

Please help!  Thanks!

---

### Post by sunrex on 2005-11-16
sudo /etc/init.d/ gdm start

 that sould work i think.. or if your getting tons of errors on everything you click like i used to to, its a memory problem, to find this out put in the kubuntu cd, reboot, when its on the place that tells you to type in server-only mode or whatever (first thing that you can type in) type in memtest then see if it has any errors, if it does and you have 2-4 memory sticks, take out one and turn it on and see if that works, if not take out the other and put back in the one you had out before, keep doing this in order, since i have had many problems with this. if there were no errors, then be glad, and figure out somthing else lol.

---

### Post by KevRus on 2005-11-16
I tried that command and got an error saying gdm isn't the default display manager, and I don't think I'm having a memory problem because Windows and Knoppix work fine, but I'll keep it in mind.  Any other tips?

---

### Post by incubus on 2005-11-17
Here's my guess: probably when you installed kubuntu-desktop, it overwrote some files that pointed to gnome.

Instead of hunting down those things, something that is good to learn but time consuming, I would simply revert to ubuntu's default by reinstalling gnome or ubuntu-desktop.

Also remember that when apt-get fetches files it keeps them at /var/cache/apt, so if you want all your space back, you can delete the KDE installation debs.

EDIT: Oh but I don't have any clue about why KDE didn't work in the first place.

---

### Post by KevRus on 2005-11-17
I tried re-installing gnome and ubuntu-desktop but I still can't log in KDE or Gnome.

---

### Post by incubus on 2005-11-17
Last thing before we try to track down the bad files: can you try to create another account and log into that?
Also, try to see what's going on in your .xsession-errors file (in the home directory).

This is just to see if the problem is in some configuration file for your account or in the whole DE system.

---

### Post by KevRus on 2005-12-04
I made another account through root but was not able to log in.  Through root I am able to start Gnome though.  .xsession-errors is empty.....So I don't really know what to tell you.  Sorry for the HUGE delay in my reply. :-P

So, how can I get gnome back up and running for my main account and completely get rid of KDE from my system?

---

### Post by metoo on 2005-12-04
You have a bunch of options:

in a console use
sudo df -h
to see if you have a harddrive space problem.

To check you system integrity use (internet connection required):
sudo apt-get update
sudo apt-get -f install
First fetch newest package list, then check system integrity, try to auto-correct found dependency issues.

If this still doesn't fix your problem try to re-install some packages:
sudo apt-get install --reinstall gdm

And other packages like ubuntu-base etc.

---

### Post by KevRus on 2005-12-04
Thank you so much!  One of the options you gave me worked, because after performing them all, I typed startx and Gnome started up like it normally would!  Thanks a lot!

And I think the problem did have something to do with disc space, because I performed df -h and I've used 13 gigs out of 14 gigs.  O_O

---

### Post by KevRus on 2005-12-04
Sorry for double-posting, but I'm still noticing a few things.

When I start up Ubuntu, the screen that shows everything being loaded still says "Kubuntu" instead of Ubuntu, KDE starts first because it still thinks it's the default display manager, and I still have TONS of KDE applications in my menus that I would like to get rid of.

Are all of these things removed by simply uninstalling all things KDE in Synaptic?

---

