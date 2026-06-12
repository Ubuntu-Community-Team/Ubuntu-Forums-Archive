---
title: "digital camera not regocnized by ubuntu"
date: 2010-01-28
forum: Hardware
---

### Post by uberbuntufan64y on 2010-01-28
I switched back to windows vista for awhile and go tused to it, and had my friend install ubuntu back on my pc, beacuse i missed it.

however now my digicam doesn't work. i'm kinda a n00berz when it comes to computers so i am trying to figure this out. what do you think?/:P

---

### Post by gordintoronto on 2010-01-28
More info, please.  What version of Ubuntu?  What brand and model of digicam?  It is helpful if you say, "I did X and Y, and expected Z, but instead, this other thing happened."

In my experience, the best way to deal with cameras and camcorders is to connect the USB cable to the computer and camera, then turn the camera on.  Within a few seconds something happens, sometimes it is just the appearance of an icon on the screen as if you attached a hard drive.

---

### Post by uberbuntufan64y on 2010-02-01
I have one that is newer. The plug seems to be secure and fit niceley. The logo has since fell off after I let a friend borrow, but I think it is Codec or something.

---

### Post by oldfred on 2010-02-01
I have never plugged a camera into any system windows nor Ubuntu. I plug the media card in. My portable has a muticard reader built in and for my desktop I built with with a multicard reader/floppy drive. I also have a cheapo multicard reader/usb device. This way I can read my cards and any friend's cards without the special cables usually required.

---

### Post by uberbuntufan64y on 2010-02-01
> **oldfred said:**
> I have never plugged a camera into any system windows nor Ubuntu. I plug the media card in. My portable has a muticard reader built in and for my desktop I built with with a multicard reader/floppy drive. I also have a cheapo multicard reader/usb device. This way I can read my cards and any friend's cards without the special cables usually required.

I need to plug my camera in to get the pictures off it because it is a digital and not a media card. This cable has worked before in vista so i think it can be made working in ubuntu because I hear that vista is hard to make work.

---

### Post by oldfred on 2010-02-01
I use several cards for my camera. It is more of a backup that way. When one card gets near full I use the other. By then I should have backed up my computer to cd/dvd so I have multiple backups, just in case. On vacation I may take both if we go berserk and take a lot of pictures.

If it is a digital camera it has a media card. Several types are used as all brands do not use the same. My reader is a 7 in 1 but I have seen much higher numbers on newer readers.

---

### Post by uberbuntufan64y on 2010-02-02
> **oldfred said:**
> I use several cards for my camera. It is more of a backup that way. When one card gets near full I use the other. By then I should have backed up my computer to cd/dvd so I have multiple backups, just in case. On vacation I may take both if we go berserk and take a lot of pictures.

If it is a digital camera it has a media card. Several types are used as all brands do not use the same. My reader is a 7 in 1 but I have seen much higher numbers on newer readers.

I do not know it has a media card what that is?

---

### Post by uberbuntufan64y on 2010-02-02
Do I need to backup CDS and DVDs to make it work? I have some blank Blue Rays so if I could use those that would be great.

---

### Post by chewearn on 2010-02-02
> **uberbuntufan64y said:**
> I switched back to windows vista for awhile and go tused to it, and had my friend install ubuntu back on my pc, beacuse i missed it.

however now my digicam doesn't work. i'm kinda a n00berz when it comes to computers so i am trying to figure this out. what do you think?/:P

Please explain in more detail what you meant by "digicam doesn't work" because this can be many things.

Some example:
1. Turn digicam on, plug into USB port.  Nothing happened.
2. Turn digicam on, plug into USB port.  Dialogbox pop-up with error message "abc..."
3. Turn digicam on, plug into USB port.  An application "def.." started but it showed an error message "ghi..."
4. Turn digicam on, plug into USB port.  An application "def.." started but I cannot find the pictures from the digicam.

---

### Post by kelvin spratt on 2010-02-02
I take it when you had Ubuntu installed before it worked ok?
are you using the same version of Ubuntu as before.

---

### Post by uberbuntufan64y on 2010-02-02
I bought new batteries for it, still doesnt work.

The order i do it is this... turn it on, plug it in, wait, nothing... ubuntu just sits there :?

---

### Post by kelvin spratt on 2010-02-02
you should plug it in before you turn it on then it sends a signal to see if it is connected to anything.

---

### Post by chewearn on 2010-02-02
> **uberbuntufan64y said:**
> I bought new batteries for it, still doesnt work.

The order i do it is this... turn it on, plug it in, wait, nothing... ubuntu just sits there :?

Ok, to find out what's wrong we need the error messages.  Here is what you need to do to find out.

1. Make sure the digicam is NOT plugged in.
2. Open a terminal window: Top Panel Menu > Applications > Accessories > Terminal
3. Plug in the digicam, wait at least 10 seconds without doing anything else.
4. Copy/paste this command into the terminal window, and press ENTER
```
dmesg | tail -n 20
```
5. You should see a bunch of text resulting from the command above.
6. Reply to this thread; copy/paste the text here.  Add [noparse]```
 
```[/noparse] tag between the text.

---

### Post by uberbuntufan64y on 2010-02-10
i find the last instructionns kind of confusing... is there any way you could dubm them down a little? i'm n00b lol k thnx

---

### Post by chewearn on 2010-02-10
> **uberbuntufan64y said:**
> i find the last instructionns kind of confusing... is there any way you could dubm them down a little? i'm n00b lol k thnx

If you can specify which part you don't understand, then I will try to explain.

---

### Post by uberbuntufan64y on 2010-02-10
> **chewearn said:**
> Ok, to find out what's wrong we need the error messages.  Here is what you need to do to find out.

1. Make sure the digicam is NOT plugged in.
2. Open a terminal window: Top Panel Menu > Applications > Accessories > Terminal
3. Plug in the digicam, wait at least 10 seconds without doing anything else.
4. Copy/paste this command into the terminal window, and press ENTER
```
dmesg | tail -n 20
```
5. You should see a bunch of text resulting from the command above.
6. Reply to this thread; copy/paste the text here.  Add [noparse]```
 
```[/noparse] tag between the text.

Why would I not want the digicam plugged in? I want it to work!:confused:

---

### Post by uberbuntufan64y on 2010-02-10
bump

---

### Post by chewearn on 2010-02-10
> **uberbuntufan64y said:**
> Why would I not want the digicam plugged in? I want it to work!:confused:

We need to capture the error message from the kernel.  In order to do that, we need:

1. Digicam to be unplugged first.
2. Then, prepare to capture the error.
3. Then plug in the digicam.

As soon as the digicam is plugged in, the hardware should trigger the kernel to detect the digicam and resolve which driver to activate.  This should occur within 10 seconds.

During the detection, any error (since the digicam failed to work, we assume there would be error) will appear in the kernel log.

Therefore,
4/5. After 10 seconds, we execute the command to read the log.

And finally,
6. You need to post the error message to this thread, so we can help you analyse what's wrong.

---

### Post by uberbuntufan64y on 2010-02-25
I still have not figured this out, ism really confused. :(

---

### Post by chewearn on 2010-02-25
> **uberbuntufan64y said:**
> I still have not figured this out, ism really confused. :(

That's too bad, sorry for your confusion.

I tried to help you as much as I can, but failing to see any useful debug information from you, my hands are tied.

---

### Post by uberbuntufan64y on 2010-03-18
still trying to resolve this :frown:

---

### Post by uberbuntufan64y on 2010-03-18
bump ;)

---

### Post by uberbuntufan64y on 2010-03-26
helperz!!! ](*,)

---

### Post by oldsoundguy on 2010-03-26
Your 15 buck camera is set to work in a Windows environment.  Time to get another camera that uses a CARD.

Then, get a USB universal card reader .. plug in type .. for under 10 bucks on eBay and be done with it.

Cheap digital cameras .. regardless of the maker, are designed to work in the Windows environment. That fact that a few DO work in Linux is in and of itself amazing! (some don't even work on a Mac!)

---

### Post by sisco311 on 2010-03-26
See if [gthumb]("apt://gthumb") detects it.

Click [here]("apt://gthumb") to install it, then go to Applications -> Graphics -> gThumb Image Viewer -> File menu -> Import Photos (or Import From -> Removable device).

---

