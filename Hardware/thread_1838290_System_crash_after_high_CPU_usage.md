---
title: "System crash after high CPU usage"
date: 2011-09-03
forum: Hardware
---

### Post by Arcken on 2011-09-03
Hi, i am here to ask u guys my problem using ubuntu and several other distros. The problem is that if i use my cpu at 100% for like 5 minutes the notebook shutdown or if i use firefox or other browser to see youtube videos and try to open something else the pc gets really slow, and even after i close firefox it continues slow, my only option is restart the system. I tried all distros possibles with most DEs but the problem is always there. I am using windows now, where this problem doesn't happens but i plan to move to ubuntu 11.10 when it gets released but i need a fix to my problem first.

Sorry for my english :)

---

### Post by |{urse on 2011-09-03
Sounds like your system is overheating, does the same thing happen with windows?

---

### Post by .... on 2011-09-03
The Flash plugin is notorious for consuming CPU. Although it's more of a workaround, try this to cut down on CPU usage when viewing online video: [http://www.webgapps.org/add-ons/flashvideoreplacer](http://www.webgapps.org/add-ons/flashvideoreplacer)

---

### Post by 2F4U on 2011-09-03
Can you give us the specification of your machine? You may try to open the case and see if there is dust inside and in particular on the fans. If there is, carefully cleaning may help to reduce overheating.

---

### Post by Arcken on 2011-09-03
> **|{urse said:**
> Sounds like your system is overheating, does the same thing happen with windows?

It doesn't. But why windows don't get so affected by overheating like linux... 

> **.... said:**
> The Flash plugin is notorious for consuming CPU. Although it's more of a workaround, try this to cut down on CPU usage when viewing online video: [http://www.webgapps.org/add-ons/flashvideoreplacer](http://www.webgapps.org/add-ons/flashvideoreplacer)

Like u said it is a workaround i need a solution for this :P,  not only flash, because the system also crash if i try to install heavy programs like Quartus II or Matlab.

> **2F4U said:**
> Can you give us the specification of your machine? You may try to open the case and see if there is dust inside and in particular on the fans. If there is, carefully cleaning may help to reduce overheating.

Its a old Acer, with Celeron 1.86 Ghz, Intel GMA x3100, 1 GB DDR, 120 HD :P . But the question is why Windows don't crash and dont gets slow like linux while doing this tasks.

---

### Post by .... on 2011-09-03
What model Acer do you have?

---

### Post by Arcken on 2011-09-03
> **.... said:**
> What model Acer do you have?

Aspire 5315-2142

---

### Post by Arcken on 2011-09-05
So... the problem is dust in the processor fan?? or something else?

---

### Post by gordintoronto on 2011-09-05
Have a look at this web page:
[http://crunchbanglinux.org/wiki/howto/aspireone](http://crunchbanglinux.org/wiki/howto/aspireone) 

specifically the section on fan control.

---

### Post by Arcken on 2011-09-05
> **gordintoronto said:**
> Have a look at this web page:
[http://crunchbanglinux.org/wiki/howto/aspireone](http://crunchbanglinux.org/wiki/howto/aspireone) 

specifically the section on fan control.

Ty alot dude :P:P

---

### Post by |{urse on 2011-09-08
I actually have an acer 5532 exhibiting the same behavior and the acerfand doesnt help, op, if you learn anything new about any of this please post new fixes, notes, ideas etc on this thread :)

---

### Post by |{urse on 2011-09-08
Hokay, just spent the better part of an hour on the phone with acer. Turns out all that I needed the latest bios upgrade (duh). The reason it works fine on windows is that the actual fan control software was never internalized in older versions of the bios. The newest update for my model internalized the fan control. So in essence the newer update for the 5532 takes care of fan control regardless of operating system. Hope this helps, ive been screwing with this problem for a while too :)

I'll post back if I see any repeated instability, but it seems to be working now.

---

### Post by Arcken on 2011-10-02
> **|{urse said:**
> Hokay, just spent the better part of an hour on the phone with acer. Turns out all that I needed the latest bios upgrade (duh). The reason it works fine on windows is that the actual fan control software was never internalized in older versions of the bios. The newest update for my model internalized the fan control. So in essence the newer update for the 5532 takes care of fan control regardless of operating system. Hope this helps, ive been screwing with this problem for a while too :)

I'll post back if I see any repeated instability, but it seems to be working now.

Did you find any changelog , cuz i have a different accer, and i think have chances that my notebook stop work with this upgrade... and BTW sorry for the late answer lolol

---

### Post by Arcken on 2011-10-08
Up

---

