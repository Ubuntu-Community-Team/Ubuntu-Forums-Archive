---
title: "Mobile 4 Series Chipset Integrated Graphics Desktop effects could not be enabled"
date: 2010-03-10
forum: Hardware
---

### Post by barrydirk on 2010-03-10
Hi All

I realise this problem has been discussed endlesly everywhere else but I still cant find a solution to the problem. I just convinced my brother to install ubuntu karmic on his Acer laptop and get rid of Windows. The thing that sold him was how much nicer my ubuntu can look with a few drops of Compiz only problem now is I cant get any desktop effects to work. 

Ive tried everything I can find in the forum and google no one seems to have a answer

Mobile 4 Series Chipset Integrated Graphics Controller

johan@johan-laptop:~$ sudo lshw -C video
[sudo] password for johan: 
Sorry, try again.
[sudo] password for johan: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:90000000-903fffff memory:80000000-8fffffff(prefetchable) ioport:50f0(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:93400000-934fffff

---

### Post by barrydirk on 2010-03-11
If could swear on this forum this would be a very long post. I have been using ubuntu for over 2 years now and I have never once encountered a problem that I could'nt find a solution to. This is only the second time I have actualy had to post a thread to get help. Is there anybody out there that can help me with this I am absolutely lost here.

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by vjgajjela on 2010-03-11
hi guys,

i got this problem while starting my pc ,
cause i have formatted the 963MB partition space from windows disk management which have been made for ubuntu i guess( apart from the 10 gb space that i have made at the time of installation). Now i couldnt able to login even into windows, there are many imp files on my windows & linux too.

can any one please help me to tackle this problem , and please try to suggest a solution by which i can save my files of windows & linux too

Thank You in advance

Vj Gajjela
:guitar:

---

### Post by garvinrick4 on 2010-03-11
> **barrydirk said:**
> Hi All

I realise this problem has been discussed endlesly everywhere else but I still cant find a solution to the problem. I just convinced my brother to install ubuntu karmic on his Acer laptop and get rid of Windows. The thing that sold him was how much nicer my ubuntu can look with a few drops of Compiz only problem now is I cant get any desktop effects to work. 

Ive tried everything I can find in the forum and google no one seems to have a answer

Mobile 4 Series Chipset Integrated Graphics Controller

johan@johan-laptop:~$ sudo lshw -C video
[sudo] password for johan: 
Sorry, try again.
[sudo] password for johan: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:90000000-903fffff memory:80000000-8fffffff(prefetchable) ioport:50f0(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:93400000-934fffff
Same chipset have to go to System/Pref/appearance
to visual effects tab. Go between the 3 selections until it decides to check for driver and click keep settings when done.
Then compiz works. Sometimes have to go between 3 settings a few times before it searches for driver.

---

### Post by Tiede on 2010-05-11
> **garvinrick4 said:**
> Same chipset have to go to System/Pref/appearance
to visual effects tab. Go between the 3 selections until it decides to check for driver and click keep settings when done.
Then compiz works. Sometimes have to go between 3 settings a few times before it searches for driver.

I have done this quite a few times. I noticed it searches for a driver when I come off a fresh reboot. Still, nothing happens, and the display is **still** unclaimed. Thus, no compiz...

It does go to "Extra", but if I close the Appearances window and open it again, it is back to "None". (The desktop effects are never seen, even when the "Extra" knob is selected).

---

### Post by reauxbeauxboy on 2011-06-27
Ok, so *really* ?!? This thread has been up here for over a year and nobody has responded?  I'm with whoever it was that wanted to cuss a blue streak about this. UGH! 

I believe this is *such* an issue because people who have this laptop (emachines 525 - 527) were looking for a bargain laptop -- and lord knows we don't want to pay more for the OS or Microsoft Office than we paid for the actual MACHINE so Ubuntu is the natural choice.  

It would be fantastic if someone could help us figure this out.  :-) I am sounding like a jerk, but I'm really just an uber-frustrated really nice guy.

I had a very difficult time installing Ubuntu at all, because for the longest time I couldn't even figure out why I was getting no install screen.  Once I figured out NOMODESET I was all good.  If people who know little to nothing about computers are now supposed to be able to download, install and configure Ubuntu -- things like this really get in the way of that.  

Anybody? Any answers?

Thanks so much!

-R

---

### Post by Duane Dan on 2011-10-23
Hi

I am having the same problem. Now Im trying to download a newer driver from [intel]("http://www.intel.com/p/en_US/support/"). I ve tryed to install compiz simple configuration without sucess. It tells me that there are dependences that could not be satisfeid (i understood that it is incompatible with unity). And if it is realy important i think you should downgrading to lucid or karmic until they solve the problem, or now try Ocelot to see if it works.

---

