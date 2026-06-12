---
title: "I type four-ten letters and it freezes..."
date: 2010-06-24
forum: Hardware
---

### Post by BiggD on 2010-06-24
Story: I've always used windows from windows 2000 to windows 7 until I started looking into open-source software recently. Well obviously Linux being the king of open-source, I thought It was time for a reformat and that Ubuntu would be worth a shot. I first tried a duel boot with Wubi and I was really impressed with what I saw. Although, I started it up and it would freeze after just typing a couple of letters in any text form. So I thought "oh, well its probably just the duel boot" and decided to just give 'er and just go with a total Ubuntu 10.04 reformat.

Problem: I'll turn on my computer and it will load perfectly fine but whenever I type in a text box, after maybe four to ten letters, it will "freeze" (even at login). Now it tends to do this maybe two-five times where I have to hard restart it and test, then hard restart again until randomly it will work.

Also, I'm not sure if it would be considered a freeze because I can open web browsers or what not at the top and even browse if I find a way with just my mouse but the applications, places, system menus won't drop down and I can't click on the shutdown button or the wireless connection icon but I can click on the date and time.

I've looked all around but I have no idea what the solution could be. If anyone has any insight on the matter, please do tell.

Thanks,

---

### Post by sikander3786 on 2010-06-24
What are your system specs? Is it a desktop or laptop?

Have you tried with some other keyboard or mouse?

I bet that is a problem with your keyboard/mouse. You might say that the same keyboard/mouse was working well with windows but I have seen this problem before.

Regards.

---

### Post by dtfinch on 2010-06-24
I had an old system several years ago that would start randomly freezing up after a short while. Another symptom was that its clock was slow, like it was missing ticks. Booting with the noapic kernel option solved the problem. I'd be surprised to see the problem on any recent system though.

If noapic fixes it, you should be able to make the fix permanent by running "sudo gedit /etc/default/grub", adding noapic to the GRUB_CMDLINE_LINUX line, and running "sudo update-grub"

---

### Post by BiggD on 2010-06-24
It's an Acer Desktop which I must of got like almost four years ago probably.

No, I have not tried another mouse/keyboard but if it differs working on windows and Linux, then it probably would be them.

But, why would it work on Windows and not Linux? and is there any way to remedy this?

---

### Post by sikander3786 on 2010-06-25
> **BiggD said:**
> It's an Acer Desktop which I must of got like almost four years ago probably.

No, I have not tried another mouse/keyboard but if it differs working on windows and Linux, then it probably would be them.

But, why would it work on Windows and not Linux? and is there any way to remedy this?

Well I don't know the answer :p Check the link

[http://ubuntuforums.org/showthread.php?t=1349147](http://ubuntuforums.org/showthread.php?t=1349147)

Regards.

---

