---
title: "Quotes, etc"
date: 2009-02-12
forum: Hardware
---

### Post by mhjones on 2009-02-12
Hello
I have just installed kubuntu on my Dell Latitude C600 (yeah, I know, it&#347; old, but still works well).

Everything is fine except:

Nowhere in any window, dialog box, terminal screen, do my quotes display.

No single quote,
No double quote,
No back quote (under tilde)
No tilde

HELP!!

I have searched the net and this site and have not been able to find anything relevant.

This has occurred in both ubuntu and kubuntu

Thanks in advance for any assistance.

Mike

---

### Post by kmac on 2009-02-12
Try a different keyboard layout? 

System >> Preferences >> Keyboard [Layouts]

---

### Post by yther on 2009-02-12
Can you see quotes that others have typed?

Here are some:  "'` »« “” ‘’ 

If you type some (I see none in your post), can others see them?

If you can't type them, I think it could be a keyboard layout problem somehow.  If you can actually type them but not see them, maybe your language environment or fonts are messed up.

**Edit:  Aha!  Look at what you typed up there...**

> (yeah, I know, it[SIZE="6"]&#347;[/SIZE] old, but still works well)

See that big &#347;?  I think your keyboard has "dead" keys.  That means, you hit apostrophe (') and then it *combines* with the next letter you type.  You should try changing layouts like the guy above me suggested, to a layout without those, or be aware of them and learn to use them.  :)

---

### Post by mhjones on 2009-02-12
Unfortunately, I did not tell the whole story.

I need to press those characters twice, and then they do not work right.
I type the following:

mkdir ¨top ten¨ (quotes keyed twice to display)

I get two directories, ¨top, and ten¨, where I should have gotten a dir called top ten

They will work in word processors, but I still need to ket them twice.

My regional settings were not correct, but I fixed those and still the same issue.  I really would like to install kubuntu and get away from windows, but I will need those characters in coding, etc, to work properly.

Thanks again,
Mike

---

### Post by mhjones on 2009-02-13
Found the issue.

I have an older laptop, and ubuntu would come up with only the minimal screen resolution.

I got an alternative xorg.conf from another thread that fixed that issue for someone else.  It does fix my resolution problem, but there are some entries for keyboard.

I commented those entries out, since my original xorg.conf did not contain those anyway.  Problem fixed.

I will post more detail when I can get to my laptop later.  Thanks to all those who commented.

Mike

---

