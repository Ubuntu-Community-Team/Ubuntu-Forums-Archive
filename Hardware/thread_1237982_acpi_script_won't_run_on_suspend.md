---
title: "acpi script won't run on suspend"
date: 2009-08-12
forum: Hardware
---

### Post by simonbonner on 2009-08-12
I'm trying to add a script to /etc/acpi/suspend.d/ to automatically unmount all cifs drives on suspend. My laptop moves with me from home to work. At home I have a samba mount which is automatically connected when I connect to the network, but isn't unmounted when I suspend. This creates problems the next time I try to suspend.

Based on the discussion at [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/24864](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/24864) I've written a script that should unmount the drives. When I run it from the command line everything seems to work properly. However, nothing seems to happen when I suspend. I've added the command 'date > /home/sbonner/TMP/test' simply to test if the script is being run, but nothing is sent to the file. I have changed the permissions on the script so that it is executable and match the permissions of the other scripts in /etc/acpi/suspend.d/.

Can anyone suggest why the script isn't being run?

Thanks for your help!

---

### Post by simonbonner on 2009-08-12
Well, no replies, but I think I've solved the problem...

Poking around in the /etc/acpi/ directory I came read the header to sleep.sh which says:
"The only time that it actually does something is when it is determined that no other parts of the system are listening (this is what the CheckPolicy call does)."

Further down there is a comment that says:
"If gnome-power-manager or klaptopdaemon are running, let them handle policy"

This prompted me to search for 'gnome-power-manager suspend' which brought me to this site: [http://en.opensuse.org/Pm-utils](http://en.opensuse.org/Pm-utils). Following the directions I created the test script, and it works. I haven't tried my unmount script yet, but it's looking promising. 

In short, the /etc/acpi interface is only used if nothing else handles the suspend event. With Gnome (and generally in Ubunt??) pm handles the event, so scripts need to end up in /etc/pm instead.

---

### Post by akin1231 on 2009-08-26
Hey there, I'm pretty new as well but I need to run a script or a command under tty7 when suspending and resuming from suspend. 

On suspend (before suspend that is) 
tty7(X-server): metacity --replace &
On resume from suspend (after full resume): tty7(X-server): compiz --replace &

This is because my Studio XPS 16 won't suspend when compiz is enabled.  

How do I run scripts or commands from certain consoles?  These commands won't work unless running from within X-server or tty7 maybe.

---

### Post by sola on 2010-10-04
@simonbonner

I am fighting with the same CIFS suspend/resume problem.
Could you attach the scripts you placed in the /etc/pm folders?
Many thanks

---

### Post by simonbonner on 2010-10-04
Hey Sola,

I'm sorry, but I'm not able to help you. I upgraded to Karmic Koala shortly after that post, and it looks like the suspend/resume system has changed significantly. It seems that unmounting is working for me now -- and I don't think I needed to change anything. I certainly make no additions to /etc/pm or /etc/acpi after this install.

Sorry about that. Good luck,

Simon

---

### Post by sola on 2010-10-04
I am on Karmic Koala myself but my systems keeps kinda-freezing if I suspend the laptop at home, take it to work and resume it.

I believe that the near-freezing behaviour is because it doesn't find the CIFS share of my home NAS (at work).

---

