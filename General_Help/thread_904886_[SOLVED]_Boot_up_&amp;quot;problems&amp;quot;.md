---
title: "[SOLVED] Boot up &amp;quot;problems&amp;quot;"
date: 2008-08-29
forum: General Help
---

### Post by Grez on 2008-08-29
This is no great shakes but the following has happened when Ubuntu boots up:

(Using Hardy Heron btw)

Splash screen loads and progress bar almost reaches the end then stalls for a short while.

The screen then changes to a text-based progress screen which is trying to start up bluetooth, comes up with 4 USB 1.1 errors of various types and then carries on into the login screens and desktop, after which things seem to go OK.

I don't have any bluetooth gear.

This first happened earlier this week, then I installed an update to Ubuntu and it stopped happening for a while. It has then started again today.

Anyone know what's happening and how I put it right?

Cheers in advance...

---

### Post by quibbler on 2008-08-30
> **Grez said:**
> This is no great shakes but the following has happened when Ubuntu boots up:

(Using Hardy Heron btw)

Splash screen loads and progress bar almost reaches the end then stalls for a short while.

The screen then changes to a text-based progress screen which is trying to start up bluetooth, comes up with 4 USB 1.1 errors of various types and then carries on into the login screens and desktop, after which things seem to go OK.

I don't have any bluetooth gear.

This first happened earlier this week, then I installed an update to Ubuntu and it stopped happening for a while. It has then started again today.

Anyone know what's happening and how I put it right?

Cheers in advance...
Try stopping any bluetooth startup programs.
Go to System-Preferences-Sessions and untick anything with bluetooth.
Reboot and see if that helps.

Regards quibbler

---

### Post by Grez on 2008-08-30
> **quibbler said:**
> Try stopping any bluetooth startup programs.
Go to System-Preferences-Sessions and untick anything with bluetooth.
Reboot and see if that helps.

Regards quibbler

Thanks for the idea.

It didn't work unfortunately.

Any other ideas please?

---

### Post by MentalNotes on 2008-08-30
I tend to find using sysv-rc-conf to turn off services works well. Install it and run it as root in a terminal. Move the cursor down to the bluetooth entry, hit - (dash) to stop the bluetooth service and remove the X marks using space in the boxes.

---

### Post by Grez on 2008-08-30
> **MentalNotes said:**
> I tend to find using sysv-rc-conf to turn off services works well. Install it and run it as root in a terminal. Move the cursor down to the bluetooth entry, hit - (dash) to stop the bluetooth service and remove the X marks using space in the boxes.

Thanks I'll bear this in mind, however....

When I booted up last time, Ubuntu did a "Routine Disk check" which you're probably familiar with, but it's the first time I've seen it do it.

Anyway, whatever it did, the problem seems to have been corrected automatically....

As a linux noob I'm quite impressed.

Thanks for the help guys. 

@MentalNotes

If it happens again I'll try your suggestion. Cheers, mate!

---

### Post by Grez on 2008-09-06
> **MentalNotes said:**
> I tend to find using sysv-rc-conf to turn off services works well. Install it and run it as root in a terminal. Move the cursor down to the bluetooth entry, hit - (dash) to stop the bluetooth service and remove the X marks using space in the boxes.


The problem started again, I followed your suggestions and it's right on the money!

Top drawer! Many thanks. You're a :KS

=D>

---

### Post by hyper_ch on 2008-09-06
another option would have been to use the update-rc.d command to remove the bluetooth damone script from the runlevels :)

now you the "thread tools" on top to mark this one as solved ;)

---

### Post by Grez on 2008-09-06
Job done.

Sorry I didn't earlier!

Still wet behind the ears but willing to learn!

:lolflag:

---

### Post by MentalNotes on 2008-09-09
@grez: You're welcome :)

---

