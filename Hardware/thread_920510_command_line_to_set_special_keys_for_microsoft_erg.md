---
title: "command line to set special keys for microsoft ergonomic 4000 keyboard"
date: 2008-09-15
forum: Hardware
---

### Post by arch0njw on 2008-09-15
_**The Issue:**_  When running VMware Workstation, my keyboard will get "bonked".  Shift, Alt, Ctrl, Super no longer work -- among a few other things.  A helpful person from the VMware community offered this command which mostly fixes the problem:

[FONT=Courier New] setxkbmap -model pc105 -layout us -option ",winkeys"[/FONT]

_**What I want to do:**_  Take this command "to the next level" so I can get back functionality in special keys that work *prior to* VMware bonking my keyboard.  These keys would be:

[LIST]
[*]Web
[*]Search
[*]Mail
[*]Mute
[*]Vol -
[*]Vol +
[*]Play/Pause
[*]Calculator
[/LIST]

_**Bonus Round:**_  If anyone knows how to get the four keys above the keypad to work (_without recompiling the kernel_) I will seriously owe you.  I loved those keys when I first got this keyboard and used it under Windows and I really miss these under Linux.

---

### Post by rajan on 2008-12-10
did you get your problem fixed? that command actually worked for me (different keyboard though). 

so you're trying to use vmware and after you start it up, the keyboard goes bananas?

---

### Post by arch0njw on 2008-12-10
> **rajan said:**
> did you get your problem fixed? that command actually worked for me (different keyboard though). 

so you're trying to use vmware and after you start it up, the keyboard goes bananas?

I did not get a complete fix to my problem.  The issue above remains as of version 6 of VMware Workstation.  What happens is if I go into a WINDOWS XP guest for any great length of time, when I leave the guest, my keyboard just does not work.

I do not have this problem with *nix guests.

Running said command restores basic keyboard functionality, but all of the cool extra keys/buttons do not work.

---

### Post by cariboo on 2008-12-10
Have a look at:

```
man setxkbmap
```

For the many options that might help you with your problem. BTW I've got the same keyboard and I haven't been able to get the zoom toggle to work in either Linux or Windows.

Jim

---

### Post by rajan on 2008-12-10
have you tried other keyboard layouts with the setxkbmap command? if you find one that works well, you should be able to have it run right after you switch back from vmware using a script. 

other options for command-line keyboard layout control are:
gconftool-2 (very nice and versatile)
gconf-editor (which is i believe just the gui for the prev command)
loadkeys 

... and the other commands listed when you "man loadkeys" 

i have many of the same needs as you do as far as quickly launching applications or modifications. in fact, i have calculator, vol +, vol -, mute, open terminal and a few others with keyboard bindings so that they work just the same as your expanded keyboard does. the control+f<X> combinations almost never have anything associated with them so they're a really good place to start. i hope you get your system working properly, but there are lots of alternatives.

---

