---
title: "[SOLVED] System Clock settings"
date: 2008-08-26
forum: General Help
---

### Post by VMC on 2008-08-26
For some reason, Ubuntu keeps screwing up my system clock.  I didn't realize it was Ubuntu at first since I check the system clock through my BIOS. I changed my battery thinking it was at fault until I realized it was always 7 hours advanced.

"System  > Administration > Time % Date" are set correctly for Los Angeles, and have been since the begining. I noticed on boot up there are two messages telling me it set my system clock. I don't know why it would set the clock 7 hours in advance and then set it correctly in Ubuntu. The time is correct while running Ubuntu but each time I reboot I have to set my system clock back 7 hours. If I instead boot up using Debian I have no problems. Something with Ubuntu.

---

### Post by fballem on 2008-08-26
> **VMC said:**
> For some reason, Ubuntu keeps screwing up my system clock.  I didn't realize it was Ubuntu at first since I check the system clock through my BIOS. I changed my battery thinking it was at fault until I realized it was always 7 hours advanced.

"System  > Administration > Time % Date" are set correctly for Los Angeles, and have been since the begining. I noticed on boot up there are two messages telling me it set my system clock. I don't know why it would set the clock 7 hours in advance and then set it correctly in Ubuntu. The time is correct while running Ubuntu but each time I reboot I have to set my system clock back 7 hours. If I instead boot up using Debian I have no problems. Something with Ubuntu.

Assuming Los Angeles is observing daylight savings time, I think that's seven hours behind UTC time. In GNOME if you right click on the date and time display (upper right), then select Preferences, then Time Settings (see screen shot attached), are you synchronised to internet server?

By the way, UTC does not mean GMT. I believe that London, England, which uses GMT also has daylight savings time. If I recall correctly, UTC is the time at the Greenwich Observatory not taking into accound Daylight Savings time.

Just asking.

---

### Post by fballem on 2008-08-26
Sorry - wrong instructions and screen shot.

Right-click on the time display, then select Adjust Date & Time.

Screenshot is below.

---

### Post by Zill on 2008-08-26
> **fballem said:**
> ...By the way, UTC does not mean GMT. I believe that London, England, which uses GMT also has daylight savings time. If I recall correctly, UTC is the time at the Greenwich Observatory not taking into accound Daylight Savings time.
I think you will find that UTC *does* equate to GMT for most practical purposes.

GMT *does not* take into account daylight saving time, which in London and the rest of the UK is referred to as BST (British Summer Time).

[http://wwp.greenwichmeantime.com/info/utc.htm]("http://wwp.greenwichmeantime.com/info/utc.htm")

---

### Post by fballem on 2008-08-26
> **Zill said:**
> I think you will find that UTC *does* equate to GMT for most practical purposes.

GMT *does not* take into account daylight saving time, which in London and the rest of the UK is referred to as BST (British Standard Time).

[http://wwp.greenwichmeantime.com/info/utc.htm]("http://wwp.greenwichmeantime.com/info/utc.htm")

Thanks for the clarification! Always nice to learn.

Thanks,

---

### Post by VMC on 2008-08-26
It's set right now to default "Manual" when try to change it states NTP not installed. Just exactly like Debian. Debian does NOT effect CMOS clock, but Ubuntu does.
I've check /etc/init.d/hwclock.sh, they both appear the same. Something in Ubuntu changes the CMOS clock even though the time is set correctly.

Edit: I rebooted in single user mode, and found a discrepancies in Ubuntu versus Debian when issuing 'hwclock'. Debian shows the correct time, Ubuntu shows 7 hours slow. Therefore I assume Ubuntu tries to compensate for it and somehow moves the CMOS clock 7 hours in advance!

This is NOT a gui related problem. I need to locate where Ubuntu fails to 'see' the correct time. It's 'hwclock' is NOT coming from my CMOS clock.

---

### Post by fballem on 2008-08-26
> **VMC said:**
> It's set right now to default "Manual" when try to change it states NTP not installed. Just exactly like Debian. Debian does NOT effect CMOS clock, but Ubuntu does.
I've check /etc/init.d/hwclock.sh, they both appear the same. Something in Ubuntu changes the CMOS clock even though the time is set correctly.

Edit: I rebooted in single user mode, and found a discrepancies in Ubuntu versus Debian when issuing 'hwclock'. Debian shows the correct time, Ubuntu shows 7 hours slow. Therefore I assume Ubuntu tries to compensate for it and somehow moves the CMOS clock 7 hours in advance!

This is NOT a gui related problem. I need to locate where Ubuntu fails to 'see' the correct time. It's 'hwclock' is NOT coming from my CMOS clock.

Two things:
[LIST=1]
[*]I believe that ubuntu stores time in UTC by default. The attached link provides a way to directly edit the appropriate file: [http://ubuntuforums.org/showthread.php?t=896447&highlight=ubuntu+utc](http://ubuntuforums.org/showthread.php?t=896447&highlight=ubuntu+utc)
[*]If you bring up the Adjust Date & Time and unlock it, you can install the NTP if you wish.
[/LIST]

Hope that this helps

---

### Post by VMC on 2008-08-26
I found the solution. I found inside "/etc/default/rcS", UTC=yes, and should =no. Debian was set to no. When I reboot now my RTC time is not effected. 'hwclock' also works correctly. I was under the impression that 'hwclock' got its info directly from RTC. Not so , apparently, but rcS effects hwclock.

---

### Post by primehunter326 on 2008-08-29
bumping this thread because I'm having a similar issue with my clock and the above solution didn't fix it.  I'm dual booting ubuntu and XP and the times don't math.  XP mirrors the system clock (as seen in the BIOS) while ubuntu is offset by a couple of hours.  changing the clock from Windows, ubuntu or in the BIOS affects all three listings.  currently Windows/BIOS have the correct time while ubuntu is off.  I tried editing the file as described above and while that put the ubunto clock closer to where it should be, it did not fix the problem.  I've had this issue for awhile and thought it was a  Windows bug until yesterday.

Edit:  Readjusting the times seems to have fixed the problem.  After editing /etc/default/rcS just adjust the time and it should match between OSes

---

