---
title: "Install stops working at bluetooth"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by x-ecutioner on 2009-04-04
i ran the Try without any change to your computer aspect today,
i pressed F6, typed nousb and hit enter (i was troubleshooting)

it then began doing the install stuff
and the same thing happened where it says:

(all other elements in list) [ok]
blue tooth

it doesnt say anything or do anything from then on.
BUT when i pressed the power down button on my desktop to exit, it stated
Stopping GNOME display manager

could this have something to do with my graphics card and not my bluetooth (honestly i dont even know what bluetooth is lmfao)?

also, as ubuntu was exiting the trying out point it said Stopping gnome display manager and did nothing else it just stoped working there

i disabled my Nvidia GeForce 8800 GT driver on my computer and experimented with the trying out process again but still the same problem happened.

even Kubuntu gives me the same problem!

any help would greatly be appreciated thanks.

---

### Post by x-ecutioner on 2009-04-04
okay well
i tried using Wubi and installing it as an App on my Windows xp profession x64 from there
all three methods of of loading ubuntu did not work for me
1. normal 
2. safe graphics mode
3. the acpi something

number two and number three produce similar errors:
here is what it says:
[12.50935] attempt to access beyond end of device
[12.509101] sda: rw=0, want=1953520065, limit 976773168
and then it shows busy box
which produces the same two errors above when i type exit

the first one (normal mode) just says
loading, please wait

ive been looking through previous posts on the forums ( many have gone through the same thing) and i dont even understand what to do... alot of suggestions include logging into the console by holding down control and delete and pressing F2 ive done this throughout all three of the loading process and it has done nothing...

any ideas anyone:(

---

### Post by x-ecutioner on 2009-04-04
okay im gonna be trying
the suggesitons of this aritcle:
[http://darinshaw.com/cs/blogs/darin/archive/2008/09/17/ubuntu-linux-boot-hangs-on-starting-bluetooth.aspx](http://darinshaw.com/cs/blogs/darin/archive/2008/09/17/ubuntu-linux-boot-hangs-on-starting-bluetooth.aspx)

ill tell you all how it goes
it seems accurate.

---

### Post by x-ecutioner on 2009-04-04
well that didnt help at the slightest

ubuntu didnt even install even with noapic in place

so i installed ubuntu in Wubi
and edited the kernel in three different modes (display acpi and normal) to make it noapic
all of them said loading please wait and did nothing

this is really starting to anger me...

any ideas from anyone?

---

### Post by tlois on 2009-04-04
recently tried wubi on a system we couldn't get partitioned to do a dual boot.  i kept having problems too.  i had to reinstall it and uninstall it several times.  and then i had some other issues and gave up on it.

are you trying it just to try out ubuntu or do you already use ubuntu?  if just trying it, I would try running it live from a flash drive or cd.

sorry i don't have any answer for you, but mainly to commiserate.  i do know that wubi has a wiki with some troubleshooting tips if you haven't looked there already.

good luck.

---

### Post by x-ecutioner on 2009-04-04
i am attempting to try it out and even when i install it through wubi it still doesnt work (meaning even trying it through the live cd doesnt wokr either).  i have not made it past the install phase which is what angers me.

---

### Post by x-ecutioner on 2009-04-07
i know there is a bump button but where is it lmfao
i can't even find quick reply

i feel so noobish right now lol

anwayys
*Bump*

anyone have any ideas why?

---

### Post by x-ecutioner on 2009-05-02
well to anyone out there experiencing the same problem

make sure all of your USB devices are unplugged beforehand
you see i didnt realize that my wireless network adapter was still plugged in
so make sure EVERYTHING
from the front and back of your computer is unplugged if youre having this same problem.

---

