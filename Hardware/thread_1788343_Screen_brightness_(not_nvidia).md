---
title: "Screen brightness (not nvidia)"
date: 2011-06-22
forum: Hardware
---

### Post by lamefox on 2011-06-22
I have a problem with my laptop where the screen brightness setting does nothing at all... and it seems this is fairly common, but I look it up and it always talks about nvidia, but those solutions don't work for me. The file they want to edit simply doesn't exist.

It's not a problem when it's plugged in but it gets so dark when I'm on battery that I often can't read things. And the bar for brightness still moves, but there's no difference made. I was just wondering, is there some way to fix this, or another way to edit it? I also tried something I found on google to set it by command but they wrote that 0 was "brightest" and when I tried that it went totally black, until I restarted. So I'm worried about trying that one anymore.

---

### Post by sanderd17 on 2011-06-22
See my signature for setting boot options, try setting the option

```
acpi_osi=
```

(so without a value)

---

### Post by lamefox on 2011-06-22
I tried this and rebooted, it brought me to a screen to select ubuntu, or ubuntu recovery mode, etc. which hasn't happened before, but I selected the regular one and it started okay. I checked the text file and it still looks like

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi= "
```

so it hasn't reverted, but the brightness function still does nothing at all, sadly. Is it safe to leave that in there, or should I take it back to normal?

---

### Post by sanderd17 on 2011-06-22
Do you have a single boot machine? In that case you can lower the timeout time to 1 or 0 seconds, than you won't be annoyed with choosing the right version of Ubuntu anymore.

I'm sorry that the acpi_osi didn't work, it's safe to leave it in there but I have no other ideas.

---

### Post by lamefox on 2011-06-22
It is but I don't find that annoying, it just worried me because it hadn't happened before.

Is there any way to set it reliably in the terminal or so? Or does the value you need to enter change with different machines? I'm not sure what went wrong the last time I tried... maybe the person making the instructions just mistyped it.

---

### Post by sanderd17 on 2011-06-22
It's normal that grub lets you choose between normal boot and recovery, but on a single boot machine you don't see grub.

Can you show me where you found the command? Maybe I can make something from it.

---

### Post by lamefox on 2011-06-22
[http://wilmor24.wordpress.com/2010/05/11/change-screen-brightness-from-terminal-ubuntu-10-04/](http://wilmor24.wordpress.com/2010/05/11/change-screen-brightness-from-terminal-ubuntu-10-04/)

That's the one I used... but 0 for me is not brightest, its just... black

---

### Post by sanderd17 on 2011-06-22
the value you should give probably depends on the type of pci card, but since it has an effect for you, can you try other values?

---

### Post by lamefox on 2011-06-22
I tried messing around with it now while I have a power source. I think FF for me is actually brightest, completely reverse to theirs. I guess I'll have to use this until/unless there is a way to fix the Fn-key shortcut.

---

### Post by sanderd17 on 2011-06-23
I'f you're happy with two brightness settings, you can create two very simple scripts and bind the fn keys to it. Just create a file with this as contents (fill in the xx).

```

#! /bin/bash
gksudo setpci -s 00:02.0 F4.B=xx

```

Make it executable (right click -> properties -> rights). Go to your keyboard shortcut settings and append a new script to it. You can make two files with two different values for each brightness.

The only problem you have is that you need to give your password to apply the brightness. There are tricks around it, but I need to search them.

---

### Post by sanderd17 on 2011-06-23
What you do to get rid of the password:

open a terminal and execute 
```

sudo visudo

```

then you will see your sudoers file. Append the line
```

username ALL=(root) NOPASSWD:/usr/bin/setpci

```
this will you make execute the setpci command as root witout being asked for your password.

---

