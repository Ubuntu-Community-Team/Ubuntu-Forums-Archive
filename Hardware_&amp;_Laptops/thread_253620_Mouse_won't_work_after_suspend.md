---
title: "Mouse won't work after suspend"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by trubblemaker on 2006-09-08
My computer will suspend when I close the laptop lid.  Everything works except the synaptic touchpad when I wake it from it's 'sleep'.  Any ideas on howto fix?

---

### Post by trubblemaker on 2006-09-14
if it helps hibernate doesn't work at all it just turns of the computer

---

### Post by trubblemaker on 2006-09-22
<after suspending>
It properly goes into a power saving mode, returns with all my programs on screen without issue but my mouse will no longer bend to my will, it just sits on my screen and laughs at me!

to add detail here is a post that I followed and I'm using it's suggested[URL="http://ubuntuforums.org/showpost.php?p=1178889&postcount=12"]
/etc/default/acpi-support[/URL]: 

Anyone know how to restart the mouse, (synaptic touch-pad)

---

### Post by matt_risi on 2006-10-13
Anyone ever get this working? It'd be really friggin cool if I could get my computer to suspend.

---

### Post by trubblemaker on 2006-10-13
bugs filed, and as far as I know no one did get it working. That had it break.

---

### Post by matt_risi on 2006-10-14
Well that's a crying shame, suspend works incredibly well otherwise. EVERYTHING resumes perfectly, just not my synaptic mouse.

---

### Post by chagrins on 2006-11-08
I have the same problem. The thing is, it used to work in Edgy, until a recent system update involving linux-restricted-modules, linux-restricted-modules-common, libmagick9 and screen. Also, Ctrl-Alt-F1, to bring up a console, doesn't work after suspend - the machine seems to totally freeze. (The mouse, and Ctrl-Alt-F1, work fine prior to a suspend.)

EDIT: I downgraded those packages, and nothing changed. I'm inclined to think it has to do with some setting I changed somewhere, but I have no idea what at present. Also, after a suspend, the machine isn't FROZEN per se, but I can't bring up a console. The screen blanks, then comes back slightly out of focus with a staticky line at the top. If I press Ctrl-Alt-F7, I can get back to my GNOME session (where the keyboard works, but not the mouse).

---

### Post by trubblemaker on 2006-11-09
good news bugs has been confirmed.  And that's good 'cause now in edgy my system hibernate, suspend don't work at all!

---

### Post by commonplace on 2006-12-26
Still no fix for this? Just setup my wife's new laptop (Compaq Presario C301NR) with Edgy, and suspend is perfect... except I can't move the mouse cursor with the touchpad when I resume from suspend. Kinda ruins it. :)

---

### Post by trubblemaker on 2007-01-17
If you guys are still having the mouse not working after suspend, and you want it to get fixed will you post output to [the bug report]("https://launchpad.net/ubuntu/+source/gnome-power-manager/+bug/80303").  

you just need to suspend:
return from suspend
record the output of:
```
uname -a >> output

sudo lspci -vv >> output

sudo lspci -vvn >> output

sudo dmidecode >>output
```
then reboot,
OK know **attach** the info to the bug report also after the reboot you can also **attach** /var/log/kern.log.0

this output will help the developers track down and kill the problem.

---

### Post by trubblemaker on 2007-04-16
issue still persists in fiesty :(

---

### Post by commonplace on 2007-04-16
> **trubblemaker said:**
> issue still persists in fiesty :(

Dang. My wife and I were really hoping this would be fixed!

/Kevin

---

### Post by mandragor on 2007-04-21
This is the only issue I have with (K)ubuntu, and it's been an issue since Dapper, possibly earlier.

---

### Post by dimeotane on 2007-04-23
Yup, similar problem here on a Dell m1210 running feisty.

After waking from a 'suspend' I lose my trackpad... so I press the key combination to "stand by" and it goes back to sleep.... then opening the lid again and I have my mouse back. Hope this bug gets fixed soon.

---

### Post by Eriol_Ancalagon on 2007-05-22
I'm having the same problem on a Gateway convertable laptop.  I'll get the exact number after I'm home from work.

Could it have anything to do with the fact that the touchpad is (internally at least) connected by a PS/2 interface?  I dunno.  My USB mouse works fine post-suspend, but that's not always ideal as a "must-have" to have with you for your laptop.

---

### Post by trubblemaker on 2007-05-23
the synaptic driver is the issue.  it's really touchy about where was and where it should be on resume , there is a rumored work around for some (didn't work for me) and a rumored fix in a kernel way down the line.  I'm sorry I don 't have the link to the bug in launchpad but it's there if I find it I'll post it.

---

### Post by methinksp on 2008-01-06
Hey,

I am running a desktop with Gusty Gibbon and have the same problem. Hibernate simply turns off the computer and the suspend supposedly turns off USB power and does not recognise my mouse after going out from suspend. If I unplug and plug the mouse cord again it works fine. Is there any progress with this bug?

---

