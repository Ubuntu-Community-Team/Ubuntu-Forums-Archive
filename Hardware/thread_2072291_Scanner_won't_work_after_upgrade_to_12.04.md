---
title: "Scanner won't work after upgrade to 12.04"
date: 2012-10-17
forum: Hardware
---

### Post by Dmoog on 2012-10-17
Hello,

I have a Canon 280. It all worked fine until I upgraded Ubuntu to 12.04. Now the printer still works normally, but when I try to scan, using GIMP or SimpleScan, the programs say 'no scanner detected'.

What to do?

---

### Post by otetiani on 2012-10-17
Check out this post: [http://ubuntuforums.org/showthread.php?t=1582497&page=6]("http://ubuntuforums.org/showthread.php?t=1582497&page=6")

Or:

have you tried scangearmp?  You may have to install it first.

---

### Post by Dmoog on 2012-10-19
OK, thanks for the link.

I have read the thread, and to be honest, it just makes my head spin. I am one of those Ubuntu users who is not especially tech literate. And I'm finding the issues with 12.04 quite frustrating.

My questions- 

I was really happy with the previous version of Ubuntu. Everything worked, it ran much more quickly and smoothly on my old machine, and I preferred the simplicity of the graphics and layout. Is there any good reason why I shouldn't revert back to it?

I have ScangearMP already installed. I don't mind launching it from a terminal. But when I do, it can't detect a scanner either. Do I need to update it? If so, with which file? Being directed to a long list of files with no obvious indication as to which one I should install, or how to install, makes my brain hurt....

I have to say, this kind of thing makes me seriously think about going back to Windows, although I hate Windows.

---

### Post by Dmoog on 2012-10-19
Update:

I have got this to work, fairly easily.

If there's anyone out there with the same problem who's as stupid as me, then here are some very simple instructions.

Go to this page
[https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages)

You get a confusing list of stuff. Scroll down to near the bottom of the page where it says 'Package Files'. 

Download the 4th from the top - scangearmp-common_1.80-0~11~precise1_i386.deb

No, I don't know what the hell the difference between an i386 and an amd64 is either but it seemed to work.

Double click on the downloaded package. It brought up ScangearMP in the Ubuntu Software Centre, which I already had installed, but it now had an 'Ugrade'option.

Upgrade.

Scanner will now work in GIMP. Open GIMP, go to File, then Create, that brings up ScangearMP. No terminal needed, no need to create any launcher.   SimpleScan and XSane still don't work, but personally I prefer GIMP anyway.

Hope that helps.

---

