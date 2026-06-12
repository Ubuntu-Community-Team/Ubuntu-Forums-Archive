---
title: "Matlab 7.6 Simulink Problem"
date: 2008-10-26
forum: General Help
---

### Post by preumbra on 2008-10-26
I have installed Matlab R2008a (Version 7.6).

Matlab and Simulik come up fine.  The toolbar on the simulink window is missing, and I can not double click on any of the simulink blocks (i get no errors - but I launch it from the launch tool).

I have Java6 installed and have tried it with OpenJDK as well.  I also have tried the fixes in the post:
[http://ubuntuforums.org/showthread.php?t=467133&highlight=simulink](http://ubuntuforums.org/showthread.php?t=467133&highlight=simulink)
Note: One person had the same problem, but it never seemed to get resolved.

I am running Ubuntu 8.04 x64

Can anyone help me?

---

### Post by preumbra on 2008-10-27
bump

---

### Post by okhascorpio on 2008-12-09
same problem here,no menue bar, no double clicks. :confused:

---

### Post by yaknowwat on 2008-12-09
You need to send this bug to the makers of the application.  We can't help really since the application isn't open source other than suggesting a different distro version or different distro.  Maybe checking their site if they state dependencies not installed or something like that.

---

### Post by preumbra on 2009-01-26
After much pain, here is what ended up.

1)Toolbar - After painful weeks with Mathworks, it turns out the Linux version of Simulink does not have the toolbar.  It seems they should have know that when I first contacted them.

2)Doubleclick - This is fixed by turning off visual effects. System->Prefference->Appearance->VisualEffects.  If someone knows a work around please post here.

---

### Post by PheonixKotori on 2009-02-28
I discovered that as far as the blocks are concerned, my mouse-wheel acts like clicking the left-mouse-button. So, put your mouse on the component, then wheel down to select, wheel down twice to open properties, or create a label, or whatever the result of a normal double-click would be. And you don't need to disable visual effects. Hurray.

---

### Post by Phongphrai on 2010-03-13
I have an annoying problem with Simulink in MatlabR2008b.  When I drag blocks from the Simulink Library Browser, my mouse pointer and the grabbed block both disappear until I release the button.  It makes very hard to place block on the model page.
  
Could it be related to another problem I have that my mouse pointer freezes a second when I copy text in clipboard?

Anyway, if anyone knows how to fix the disappearing thing, thank you a lot in advance!

---

