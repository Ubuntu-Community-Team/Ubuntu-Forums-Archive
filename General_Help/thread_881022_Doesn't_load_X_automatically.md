---
title: "Doesn't load X automatically"
date: 2008-08-05
forum: General Help
---

### Post by blazemore on 2008-08-05
When I start up, I get dumped at a command-line logon prompt.

I log in, and run 'startx', and I'm fine.

This is annoying, how can I make it do it automatically?

---

### Post by loboc on 2008-08-05
try ```
sudo dpkg-reconfigure gdm
```

to reset the login manager

---

### Post by Qchan on 2008-08-05
> **blazemore said:**
> When I start up, I get dumped at a command-line logon prompt.

I log in, and run 'startx', and I'm fine.

This is annoying, how can I make it do it automatically?

[b][color=darkred]
You're probably booting through the Recovery console. When your PC boots, be sure to press ESC to view the Grub boot menu. Make sure you choose the correct mode.
[/b][/color]

---

### Post by blazemore on 2008-08-05
1) Won't sudo dpkg-reconfigure gdm reset other settings?
2) I'm running normal, not recovery. Good point tho if anyone else has a similar problem.

---

### Post by Qchan on 2008-08-05
> **blazemore said:**
> 1) Won't sudo dpkg-reconfigure gdm reset other settings?
2) I'm running normal, not recovery. Good point tho if anyone else has a similar problem.

[b][color=darkred]
Check the kernel boot options. Make sure there isn't anything foreign in there (like recovery)
[/b][/color]

---

### Post by markthecarp on 2008-08-05
> **blazemore said:**
> 1) Won't sudo dpkg-reconfigure gdm reset other settings?

It should only reconfigure gdm. My first thought was you don't have gdm installted. I had to remove gdm to make a machine boot in the way you describe. Long story on why I _wanted to do that...

> 
2) I'm running normal, not recovery. Good point tho if anyone else has a similar problem.

---

### Post by KatBuntu on 2008-08-05
> sudo dpkg-reconfigure gdm
That's the way this issue is solved, it won't reconfigure another stuff just gdm. 
 
Are you sure that you're runlevel is by default 5 in your /etc/inittab?

```
# The default runlevel is defined here
id:**5**:initdefault:
```

---

### Post by loboc on 2008-08-05
> **blazemore said:**
> 1) Won't sudo dpkg-reconfigure gdm reset other settings?
2) I'm running normal, not recovery. Good point tho if anyone else has a similar problem.

It wont even change you theme.

Try
```
 sudo /etc/init.d/gdm restart 
``` 

to check it after you do the reconfigure

---

### Post by blazemore on 2008-08-06
I did reconfigure, and it worked fine. Run level is 5. I don't know what the problem was but who cares; I know what the solution is!

Solved.

---

