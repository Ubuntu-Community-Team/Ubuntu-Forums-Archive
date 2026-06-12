---
title: "Keyboard Issues"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by azelter on 2007-01-07
Hi All,
I have a Dell 710m and am running edgy. I have an issue where sometimes when I press a key, the computer behaves as if the key was held down for a long time. This can happen with any key. Most of the time everything is fine. This also happened when I was running the previous version of Ubuntu. I see the following in /var/log/messages but don't know if this is relevent:
Jan  6 21:16:31 localhost kernel: [17188592.340000] atkbd.c: Unknown key release
d (translated set 2, code 0xe0 on isa0060/serio0).
Jan  6 21:16:31 localhost kernel: [17188592.340000] atkbd.c: Use 'setkeycodes e0
60 <keycode>' to make it known.
I am not running windows so I don't know if this is a hardware issue or a software one.
Any suggestions of how to solve this problem or where to look to find out more information would be much appreciated.
Alex

---

### Post by cfischer on 2007-01-26
I have the same problem. Are we the only ones? I have a Dell Inspiron 5150 running edgy. 

And now, the keyboard has begun shutting down - I can only type caps: !@#$%^&*() for 1234567890 so I can't even go to a terminal and type reboot. At least the mouse continues to work.

Charlotte

---

### Post by azelter on 2007-01-27
I have been looking around and there seem to be alot of other people who have had similar problems. It seems there are many causes and in each case it is difficult to find out what the problem is. As mine is only a minor irretation I have left it for the moment - hoping that feisty will cure it... no time to mess around.

---

### Post by firstc624 on 2007-01-27
i as well have this issue.  i am running a hp dv5040us series laptop so i don't  hink it is brands aor laptop specific.

---

### Post by azelter on 2007-01-27
Yes, I have read about it on many types of laptop running linux. There just seems to be nothing in the log files to debug it though. I wonder if X could be started in some kind of verbose logging mode that would help to identify the problem.

---

