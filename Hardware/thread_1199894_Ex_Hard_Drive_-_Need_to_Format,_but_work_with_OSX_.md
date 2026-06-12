---
title: "Ex Hard Drive - Need to Format, but work with OSX too?"
date: 2009-06-29
forum: Hardware
---

### Post by zacharyrs on 2009-06-29
I have a hard drive that has a ton of info from my MAC OSX previous life. I have given up trying to make my hard drive work with Ubuntu (HD shows up as Read-Only, and I can't change this - other forum posts recommend just re-formatting it), and I am now going to focus on moving my documents from this hard drive to a staging area, format the HD, and then put the files back on there.

My question is how can I format the HD so it will work in both Max OSX and Ubuntu environments? Any/all help will be greatly appreciated.

---

### Post by kidders on 2009-06-30
Hi there,

As you probably know, OSX creates journalised HFS+ filesystems by default. For some reason, Linux doesn't fully support journalised HFS+, which is probably why you haven't been able to write to your MacOS filesystem.

One possible solution is to strip the journal away. Unfortunately, the other thing Linux lacks is a complete set of HFS+ utilities, so you'll need to use MacOS to do it.[LIST]
[*]I suggest plugging your hard disk into a Mac & checking the filesystem over with the Disk Utility first. That way, you can be sure it's in good shape before you drop the journal.
[*]Stripping away the journal will boost your write performance, but it'll also make the filesystem a bit more prone to corruption in the event of a sudden power loss.
[*]Just FYI, it's not appropriate to use HFS+ as a root filesystem for Linux, but you could mount it at /home or something.
[/LIST]

> **zacharyrs said:**
> I am now going to focus on moving my documents from this hard drive to a staging area, format the HD, and then put the files back on there.That's only necessary if you can't get your hands on a working OSX installation. Without MacOS, there is no safe way of converting a journalised HFS+ filesystem into an unjournalised one ... you'd have to go with your current plan instead.

One additional suggestion I would make is to try to ensure your user IDs are the same on your Mac and your Linux box. That way, files you create using one OS will wind up being owned by the corresponding account on the other one. A typical Linux OS will start numbering user accounts from 1000, whereas OSX tends to start at 501, so out of the box, both OSs will moan at you endlessly about not having permission to do things. If you can, I'd recommend changing your OSX account's user ID, so it matches your Linux box (ie not the other way around).


I hope that helps.

---

