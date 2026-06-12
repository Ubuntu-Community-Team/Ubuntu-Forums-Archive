---
title: "2 Keyboard Ponderings"
date: 2008-07-18
forum: General Help
---

### Post by Tom_ZeCat on 2008-07-18
**Pondering 1:**
I'm using a Microsoft Digital Media Pro Keyboard like the one in this link:
[http://pcpowerzone.com/midimeproke.html]("http://pcpowerzone.com/midimeproke.html")

I'm using a KVM switch to use this keyboard (and my mouse) with a Windows XP Pro PC and an Ubuntu 8.04 one.  I don't know if you can see in the photo, but the keyboard has several hot key buttons such as "My Documents," "My Pictures," "Messenger," "Calculator," "Mail," and others.  The software that comes with the keyboard automatically assigns those buttons to programs on the system.  For instance, the Mail one is assigned to Outlook Express.  Fortunately, the software lets you change the key assignments to whatever you want.  For example, I changed the Mail one to Thunderbird.  

There are also 5 unassigned keys, simply labeled 1 through 5, which, as you may guess, you can assign to whatever.  

On my Linux PC, the keyboard's Calculator button pulls up the Linux calculator.  Cool, that's what I want.  However, the other buttons don't do anything.  I'm wondering if there's some way to assign these keys to what I want, including the 5 non-preassigned ones.  

System ===> Preferences ===> Keyboard ===> Layouts and looked under Microsoft for "Microsoft Digital Media Pro Keyboard," but didn't find it.  I did find several other models.  Someone has definitely done some work on using MS keyboards with Linux.  That makes me wonder if there's a Linux driver for my keyboard somewhere.  

I don't know if it's relevant, but I switched the Ctrl and Caps Lock keys in Ubuntu's keyboard choices.  (I also switch them on the Win XP machine via a driver named CtrlPlus.)  

**Pondering 2:**
I also wonder if there's some way to use the Windows key under Linux.  In Windows I use that key for numerous shortcuts via a program named WinKey.  For example, Win+N brings up Notepad, Win+[spacebard] brings up Wordpad.  I use some other combos too: Shift+Win+L brings up Lotus Word Pro while Shift+Win+F brings up Final Draft.  I use these programs a ton, so those hot keys save me a lot of time.  

Is there some way to use my keyboard's Windows key for customized hot keys under Linux?

---------------
**Edit:**
I'm such a goofball.  Right after I posted that I figured out how to assign the keys I asked about in **Pondering 1**.  In case someone does a search and gets this thread, I'm putting the answer here.  It's System ===> Preferences ===> Keyboard Shortcuts, then you click on a function you want to assign and hit that key.  

Looks like I still can't assign the 5 unassigned keys, at least not via that route.  I'm going to still look for a way to do that.  I'm also still looking for a way to use the Win button for hot keys as described in **Pondering 2**.

---

### Post by pauper on 2008-07-18
Here is a good tutorial regarding multimedia keys:

[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)

You can assign any key to do whatever you want. But be careful, don't mess
things up for yourself. In case you can't bind some keys via metacity you can
use xbindkeys:

```
sudo apt-get install xbindkeys
```

---

