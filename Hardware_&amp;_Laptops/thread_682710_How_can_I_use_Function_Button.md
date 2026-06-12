---
title: "How can I use Function Button"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by Hoom@n on 2008-01-30
Hello!
I wanna set some shortcuts with my laptop function button, e.g. Fn+F3 for mute. But in keyboard shortcuts when I click on mute and press Fn+F3 nothing happen. (It works for other buttons and it has just problems with Fn) What can I do?
Thank you,

---

### Post by cdtech on 2008-01-30
Which laptop do you have?

Some keys just work, because they are hardwired. The other keys can be devided into 2 categories:
the keys that are recognized by the kernel, and those that are not.

To be able to program the keys, they must be recognized by the kernel.

To see which keys are recognized by the kernel, you run

```
xev
```

---

### Post by Hoom@n on 2008-01-31
Fn button doesn'n work! No way to slove it?

---

### Post by cdtech on 2008-01-31
Some keys just work, because they are hardwired. I have the same FN key and all of mine execute (do what their labeled to do).

Some FN+fkey's do nothing and will let you know with an error in a log file, such as :

--------------------------------------------------
kernel: atkbd.c: Unknown key pressed (translated set 2, code 0xf4 on isa0060/serio0).
kernel: atkbd.c: Use 'setkeycodes e074 <keycode>' to make it known
--------------------------------------------------

These are the scancodes (e074). You can view this file while you press the unresponsive key combination to see if the kernel does see the combination. In the terminal type :

tail -n 0 -f /var/log/messages

If you use xev and see nothing from the combination that could mean that there are no keycodes associated with that combination. Just check the log file. The code you see from xev (in the terminal) are the keycodes.

So if you see the error message in the log file you can attach a keycode to it.

The keycode to attach to a scancode can be found in /usr/include/linux/input.h

Some undefined keycodes ; 84, 120, 195-199, 239

The command to set: `setkeycodes <scancode> <keycode>`

After its set you can assign it to what ever you like.

---

### Post by Hoom@n on 2008-01-31
Hello! Really thank you for your helps. First I've to say please take a look at [http://ubuntuforums.org/showthread.php?t=682673](http://ubuntuforums.org/showthread.php?t=682673) In that topic I said that I found that when I unplug my laptop the LCD light reduse. So I wanna assosiate that control to Fn+f5. How?
+++
When I use xev and I press Fn or Fn+Fx (x:num) I get notthing. Like I didn't press any key. And I couldn't use what you said in the last post. Could you please explain it?
___
Thank you.

---

### Post by cdtech on 2008-01-31
Type in a terminal :

tail -n 0 -f /var/log/messages

This will show you any error message developed by pressing that key combination.

Press your FN+f5 key while the terminal is running. If you see an error code (like the one I showed you) then it is possible to set a keycode to that combination.

**EDIT::**

If you just want to set your brightness on your screen, you can do that in the "Gnome Configuration Editor".

Go to Applications > System Tools > Configuration Editor. In the left pane : /apps/gnome-power-manager/backlight/ and you can adjust the display there.

Is this what your looking to do?

---

### Post by Hoom@n on 2008-01-31
Nothing happen when I press Fn+something (It workde for ctrl(or alt)+something) So you mean I can do nothing on this button in linux. Ok, but how can I find that backlightcontrol? As I said when I unpluged my computer the light redused and I saw a window which has a sun and a thing like ||||||||----- and when I plugedin my computer I saw that again but with ||||||||||||| shape. **How can I access that to adjust the light?** I gonna get blind if I don't adjust the light! And I can't work everytime with unpluged computer. My batty works only half an houre!
Please help and Thank you.

---

### Post by Hoom@n on 2008-01-31
Oops! I found the brightness applet and added it to my panel and there is no problem, Just this: When I plug my computer I can't see the charging. I know I can add it. But I wanna see it at place which it was before. (when I unplug and i'm on battry I can see it but when i'm on AC power I cant see it)
Thanks.

---

### Post by cdtech on 2008-01-31
> **Hoom@n said:**
> Oops! I found the brightness applet and added it to my panel and there is no problem, Just this: When I plug my computer I can't see the charging. I know I can add it. But I wanna see it at place which it was before. (when I unplug and i'm on battry I can see it but when i'm on AC power I cant see it)
Thanks.

You wont see it when the battery is fully charged, it goes away. Its only visible if its charging.

---

### Post by Hoom@n on 2008-01-31
OK, again thanks.

---

