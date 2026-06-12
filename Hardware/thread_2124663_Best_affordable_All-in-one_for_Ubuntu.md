---
title: "Best affordable All-in-one for Ubuntu"
date: 2013-03-11
forum: Hardware
---

### Post by AllNamesRTaken on 2013-03-11
Hello,

I was thinking of getting an AIO computer for development as well as all around media consumption and stuff (since my virtualbox isnt working they way I want it with opengl and QtQuick). Sadly I realize that my budget is as always strained so some $1800 monster is not really an option. Anyhow there's of course System76 and their 21.5" sable but theres also Vizio's 24" and 27" things, and probably theres many other out there.

My question is mainly which will work with ubuntu and which wont. System76's computers should of course work but the Vizio is 27" and better graphics for pretty much the same price.

Does anyone have any experience with these or any other AIOs?

Thanks,
J

---

### Post by Tiede on 2013-04-14
I am not sure if this is too late.
I own a Vizio AIO 24" (CA24-A4) and I must forewarn you, if you are planning on getting one of those, you will have problem with the input devices.
While **everything else** will work out of the box, Vizio's mouse is somewhat weird with the way they implemented left and right click events, so it will behave somewhat oddly in Linux, because left and right clicks are computed based on the location of your finger when clicking, (picture a touchpad interface) but with physical buttons underneath that register the "click". That makes drag and drop really *interesting* - to not use a more ordinary word - in linux.

The mouse thing is of course, just an annoyance. But the keyboard is completely kaput. It will work within grub bootloader, but only the meta, shift and ctrl keys will be recognized by X11. I'm still awaiting a fix for that one, and that's actually the reason why I have Win7 on the AIO instead of linux... :( Can't work without a keyboard, can I?
Sad part is I don't even have a USB keyboard lying around I could use to hook it up as a temporary fix... but I digress.

Also, if you still haven't decided and are considering getting this, just be advised that typing on the keyboard will take a little time to get accustomed to. It's not at all a bad experience, it's just somewhat oddly squared. But it looks and feels nice. The only other downside would be the lack of home, end, page up, page down and scroll lock buttons. That is correct, they are not at all available, not even via the Fn key. Why? I don't know what Vizio was thinking at the time. Needless to say, that is one big annoyance for me, even within windows, as I rely on these keys even more than I realized myself!

Everything else, like I mentioned above, will work out of the box in ubuntu, to include sound, camera, wifi... you name it! So if you were planning on using your own solution for mouse and keyboard, then I say go for it. Otherwise, steer clear (for now).

---

