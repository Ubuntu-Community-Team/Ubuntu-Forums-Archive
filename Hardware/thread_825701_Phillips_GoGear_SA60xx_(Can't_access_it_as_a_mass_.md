---
title: "Phillips GoGear SA60xx (Can't access it as a mass storage device)"
date: 2008-06-11
forum: Hardware
---

### Post by linuxmademecrazy on 2008-06-11
How do I access a gogear SA60xx as a mass storage device? I have usbmount installed, and it doesn't mount it as a mass storage device. I can access the device with MTP (Media Transfer Protocol), but I have more than just MP3 files on the device, so MTP doesn't pan out too well. The device will work as a mass storage device, I just don't know how to make ubuntu opt for mass storage over MTP.

---

### Post by chewearn on 2008-06-11
As far as I know, Philips gogear device don't support USB mass storage, especially when Windows XP or Vista, and Windows Media Player are stated as the requirements on the packaging box.

The way I see it, you have two choices:
1. contact Philips; complain loudly :mrgreen: if they do not give a good solution
2. maybe you can use gnomad2 to do the copying via MTP; not sure if it would work, but you can give it a try.

---

### Post by linuxmademecrazy on 2008-06-11
> **AstalaVista said:**
> As far as I know, Philips gogear device don't support USB mass storage, especially when Windows XP or Vista, and Windows Media Player are stated as the requirements on the packaging box.
Ah..... I saw mass storage interface in device manager and assumed otherwise.

> **AstalaVista said:**
> The way I see it, you have two choices:
1. contact Philips; complain loudly :mrgreen: if they do not give a good solution
[Begin microsoft related joke] I would call them, but I can break my $100 USD mp3 player without telephone support. I don't need a indian guy telling me to "pick up sledge hammer" and "slam the hammer head into the mp3 player vigorously." I can accomplish that with minimal thinking. [End microsoft related joke... horrible support memories....]

I did and they never responded to my emails. I'd call them, but I'm a pure internet junkie, I have no phone..... who would I, or better yet, who would call me? xD

I flooded their email inbox, if it exists, with hate mail and descriptions of the problem that caused me to hate them.

> **AstalaVista said:**
> 2. maybe you can use gnomad2 to do the copying via MTP; not sure if it would work, but you can give it a try.
[On a serious note] I have files that are not inside the "music" directory of the mp3 player, which, this tool only seems to access the things in the "music" directory. I need to access personally created directories. I have a full back up of a website in the device, which I really need to access, because it's the only copy that exists.... it would suck if I can't access it ever again =/. Are there any other alternatives?

---

### Post by chewearn on 2008-06-11
In the gnomad2, the third tab is Data transfer, which is supposed to give you access outside the music directory.  At least, that's the way it appear on my Creative Zen (with exception that every files are listed in one flat main directory).

Else, I don't see any other way, but to find a Windows machine.

---

### Post by linuxmademecrazy on 2008-06-11
I see only what I've got in the music directory. It shouldn't be hard to overlook, because it's more than 50 files with .php extentions..... even though I have like 2,500 songs.... it should stand out, but, with that aside, I need to preserve the directory structure too, because I don't remember where every single file belongs (and I really don't want to have to read through that much php.... it's a lot of code). I'm really regretting using this for a storage device now. xD

---

