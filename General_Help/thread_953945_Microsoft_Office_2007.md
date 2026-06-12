---
title: "Microsoft Office 2007"
date: 2008-10-20
forum: General Help
---

### Post by bluefire27 on 2008-10-20
I tried running the Microsoft Office 2007 Trial but it doesn't let me since ubuntu isn't Microsoft. Is there any way at all that I can get the trial for free and that I'll be able to use ALL the components included?

Thanks.

---

### Post by beno1990 on 2008-10-20
Why not just use Open Office?

It's free and works natively on Linux, and has all the same functionality as MS Office.

---

### Post by bluefire27 on 2008-10-20
I tend to prefer the PowerPoint programs that are used on Microsoft. Openoffice.org WORD PROCESSOR is definitely better than Microsoft Word though. That's why I tried installing the trial.

---

### Post by CloudFX on 2008-10-20
Running Office 2007 will not work with Ubuntu.  Your only option would be to try it with Wine, but I doubt you will have success.  I myself have not tried this.

```
sudo apt-get install wine
```

To install Wine.  For more information, please see [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine).

However, I suggest you just stick of OpenOffice.org.

---

### Post by Monotoko on 2008-10-20
Why dont you try a duel boot with windows? Then you could have Microsoft Office, etc on windows, and the other stuff on Ubuntu?

more info:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Fixman on 2008-10-20
You can use Microsoft formats with Ubuntu by (file->save as), however, it won't work with wine.

---

### Post by leehach on 2008-10-20
According to WineHQ, PowerPoint 2007 installs and runs, with some configuration editing required.  See here for more information:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813)

I have PowerPoint 2003 installed on Wine, and it works reasonably well, but some things, like choosing slide layouts, don't seem to work.

I've found that OpenOffice Presentation is not quite compatible with PowerPoint files.  Font sizes are inconsistent: you open the file in Presentation and text may overrun the text box or slide, but you open it in PowerPoint and it fits just fine.  Some animations don't work (movement paths, in particular).  If you edit the file in Presentation and save to the PowerPoint format, it seems to strip out the animations it doesn't understand.

If you're doing this on files you'll be displaying on your own laptop, this incompatibility doesn't matter.  But if, like me, you edit the files at home and then show them in venues where the computers only have PowerPoint, then you need to edit them in PowerPoint.

Another option is to run PowerPoint in a Windows virtual machine.  I just installed VirtualBox on my computer and found it to be not painless but not to difficult either.  This option is the most heavy lifting, but gives you a perfectly functional PowerPoint install without having to dual-boot just for one application.

--Lee

---

### Post by davidcrew on 2008-10-21
Wow, I love reading these forums. I didn't even know that it could work under wine. I'm still sticking to OpenO personally :D

---

### Post by hyper_ch on 2008-10-21
you could also install windows in a virtual machine (vmware / virtualbox)

---

