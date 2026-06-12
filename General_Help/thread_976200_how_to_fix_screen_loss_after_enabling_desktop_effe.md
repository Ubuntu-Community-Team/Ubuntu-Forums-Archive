---
title: "how to fix screen loss after enabling desktop effects"
date: 2008-11-09
forum: General Help
---

### Post by pbg on 2008-11-09
Hi 
I have used several releases of k/ubuntu and I upgraded to Intrepid Ibex this week. 

I had a screen loss when playing after checking on enable_desktop_effects settings for the desktop. I was at the dialog window at: 
start menu > system settings > desktop > desktop effects > enable desktop effects.

After enabling the selection, the screen went black. Mouse was visible. I rebooted, got the login screen, logged in, screen goes white, then black. 

I saw a description of a similar problem at this link:

[http://ubuntuforums.org/showthread.php?t=621561](http://ubuntuforums.org/showthread.php?t=621561)

The problem and solution posed are almost the same as in my case.

What made a difference, and got my display back, was this:

choose console login

at the command line, remove the .kde folder:

rm -rf .kde

sudo reboot

 That is, remove the .kde folder in a terminal session and then reboot. Then I was back in business. 

The new desktop for kubuntu intrepid ibex looks slick but as far as I am concerned there are controls that I was familiar with in earlier versions of kde and kubuntu that I feel are missing altogether in this new release. For example, how can I set a different background for desktop 2? Stuff like that has been moved or disappeared in this latest release.

---

### Post by LorneLReap on 2009-03-02
Thanks for the information, this fix worked very well, I beleive it has to do with the double head...just trying to work out disableing svideo in xorg.conf

---

