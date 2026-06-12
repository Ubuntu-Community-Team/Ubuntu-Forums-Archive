---
title: "Laptop problems"
date: 2009-03-02
forum: Hardware
---

### Post by silvagroup on 2009-03-02
Well after looking for months on the net I have tried everything possible with no really good result or answers.

I have a HP dv5 4gb ram 500gb disk intel graphics and Intrepid.

My swap partition is set to 10gb.

When I hibernate the system just does a shutdown? That's not what hiberante should do, I can just do a shutdown if that's what I wanted.

If I do a suspend it does something but when I try to get back in the screen is totally black screen. I tried crtl-alt-bcks and it goes into a never ending error message about zen (not running it) ata problems.
Crtl-alt-delete does the same, I have to do a power off and reboot.
In all tis experimenting I have been lucky my system has been totally messed with all this powering off.

I know it just Ubuntu because, being cautious I set up the system for dual boot and of course it all works fine in Windows.

Sadly laptops are the only place I run windows. 

Any help with this would be greatly appreciated so I can get rid of windows form my laptop also.

---

### Post by 00b00nt00 on 2009-03-02
Hiberante shuts down your system by first saving the contents of the computer's RAM to the hard disk. That way, when you re-start, the computer will appear as it was before you selected hibernate.

Personally, I think the hibernate function is rather unsatisfying, why not just shut down?

Suspend will switch off most of the components, except RAM. This is useful because you can leave your computer for a few hours, and it will (should) awaken at the touch of a button. However, if there is a power failure, you will lose whatever you were doing on the computer at that time (assuming you didn't save).

I suggest that if you can't get suspend to work, disable it and tell power management to turn of the display instead. Your computer will still be running, so you will have to remember to shut down at the end of the day.

---

### Post by silvagroup on 2009-03-03
I love Ubuntu, let me qualify that, on the desktop. And it works well with my laptop, most things worked "out of the box" and with some minor tweaking almost everything works. Still need to do more tweaking to get all my extra laptop capabilities working, such as remote, extended keyboard functions and some other niceties. 
However this again takes it out of the realm as a serious OS for those who really just want it to all work out of the box, and that's 90% of the users.

> Hiberante shuts down your system by first saving the contents of the computer's RAM to the hard disk. That way, when you re-start, the computer will appear as it was before you selected hibernate.

Unfortunately that's not the way my system works, I it does a shut down and then it's a boot up when I come back. Nothing is in it's previous state.
Suspend just does not work !!!! System goes into a unstable state and nothing but a power off gets me out of it. I have tried everything possible from Googling on the matter and it's still a useless function, except to create a system crash.

Unfortunately, and this is not a plug for Windows, but here Windows does it right, when I power my system back on after hibernate/suspend it takes me exactly back to where I left off, everytime. I don't have to log back in and what ever programs were running still are, even to the point of where my cursor was when I closed the lid. 

> Personally, I think the hibernate function is rather unsatisfying, why not just shut down?
 From what I have experienced that is all it is doing.

In Ubuntu these functions both are pretty useless in there current state, and if there is no solution around these things this really makes Ubuntu a minimal player in the laptop OS market. And Linux as a whole unless there is a distro out there that does these right.

What I was hoping with this post was to find some answers to these short comings.

This is really a very weak point Ubuntu, and you would be surprised how many remarks I get, and rightly so, because I talk up Ubuntu so much to all my colleagues and friends but every time I have my laptop around, Windows is the primary OS and I have to explain, well Ubuntu is great except for some limitations on laptops.

Which doesn't make for very many converts.

Again any help with this would be great, as I would love to totally loose Windows.

Or if anyone knows of a Linux distro that is 100% functional with Laptops that would be great also.

---

### Post by silvagroup on 2009-03-03
Sorry but in my quest for the perfect Linux laptop distro I came across this [http://blogs.techrepublic.com.com/opensource/?p=175]("http://blogs.techrepublic.com.com/opensource/?p=175") interesting article, kind of echoes my frustrations with this critical issue for laptops.

But I also ran into this [http://www.linux.com/feature/114220]("http://www.linux.com/feature/114220")which seems like it could offer some solutions, however I have no idea to do this with Ubuntu specifically and because of limited knowledge would take a long time to figure it out.
So it would be great of one of the Ubuntu gurus could take this and make some thing of it for *buntu distros.

I also saw, and can't recall, where that wlan should also be shut off and restarted when restoring system, and that was a problem with my specific system because I cant' seem to find my wifi card it's not wlan0. What a pain.

So if some one would be willing to tackle this it would be a great boom to *buntu.

---

### Post by Mauser1891 on 2009-03-03
Hello Folks,


I am curious as why one would 'hibernate'?
It's a point between uptime, and shutdown.  Linux is a uptime OS.
Just set your 'power management'/screen saver, and just let it be.
I use a Compaq C551NR Laptop.  It's down when I am mobile, and it's on the rest of the time.

---

### Post by silvagroup on 2009-03-04
> I am curious as why one would 'hibernate'?
It's a point between uptime, and shutdown
Time, and hd access which both translate to power saving, and when on battery that matters allot.
With hibernate using XP my system restart drops by 2/3rd the time and disc access is reduced greatly thereby improving battery and in the long run it's probably increasing disk life also.

---

### Post by 00b00nt00 on 2009-03-06
One final thought. Root through the log files, and see if there are any error messages posted, particularly related to the Intel chipset.

---

### Post by silvagroup on 2009-03-06
Sounds reasonable, will root around and see what comes up.

---

### Post by 00b00nt00 on 2009-03-06
I found this in the Ubuntu release notes:

"Hangs with desktop effects on Intel 830MG and 845G video cards

There is a bug in the Intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and will freeze the system. For new installations, please install using the safe graphics mode (press F4 in the startup screen) on these systems and disable desktop effects via System -> Preferences -> Appearance, clicking on "Visual effects" and choosing "None"."

Maybe this affects you?

---

### Post by silvagroup on 2009-03-14
Sorry it took so long to respond, tried it still crashes system.
Would really be nice to see the *buntu folks put some effort into making the OS work on laptops too.
Oh well sadly Vista will just have to stay on and I'll have to stop bragging about *buntu and eat some crow.
Thanks for your effort.

---

