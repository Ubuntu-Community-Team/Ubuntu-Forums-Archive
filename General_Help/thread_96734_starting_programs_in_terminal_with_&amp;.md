---
title: "starting programs in terminal with &amp;"
date: 2005-11-29
forum: General Help
---

### Post by yohan on 2005-11-29
I tried starting programs with & for instance:
gedit &
and i get the output:
[1] 9372
which means the PID I guess. But the problem is that when i close the terminal the program also closes. Why is this? & is suppose to start a seperate thread right? Is there anything im doing wrong? Im using ubuntu 5.10 with openbox...its the same in all terminals. 

Yohan

---

### Post by ranf on 2005-11-29
[QUOTE=yohan]I tried starting programs with & for instance:
gedit &
and i get the output:
[1] 9372
which means the PID I guess. But the problem is that when i close the terminal the program also closes. Why is this? & is suppose to start a seperate thread right? [/QUOTE]
& puts a program in the background. So you can use the terminal for other stuff.
But the terminal is still sort of the master to this gedit instance. When it's closed it sends some signal to any child processes.

To get around this, use:
```
nohup gedit &
```

---

### Post by yohan on 2005-11-30
Thanks for the reply ranf...I tried that and its no difference. I tried using gnome and that doesnt make any difference. Has anyone experienced this? It works fine at school where we use red hat fedora core.

Thanks...

---

### Post by hw-tph on 2005-11-30
Just exit the terminal gracefully instead of clicking the close button: Use the **exit** command, or faster and better: Ctrl+D (end of file character)


H&#229;kan

---

### Post by yohan on 2005-12-03
thank you! It worked! 

Why is it that it doesnt work by clicking the close button? Can I change the default close operation or something? 

Thanks!!

---

