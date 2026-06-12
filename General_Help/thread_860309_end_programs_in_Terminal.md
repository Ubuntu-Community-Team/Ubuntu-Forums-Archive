---
title: "end programs in Terminal"
date: 2008-07-15
forum: General Help
---

### Post by CaseyCaseyCasey on 2008-07-15
Hi

Could anyone tell me if there is a command to end programs that are running on ones computer (for instance, FireFox, Skype, Pidgen etc... ) just by using a command in the Terminal and adding a modifier?

I'd really appreciate it if you could point me in the right direction on this one.

---

### Post by Kevbert on 2008-07-15
You could try
```
killall *filename*
```
where filename is the program you want to stop.

---

### Post by houbysoft.xf.cz on 2008-07-15
Huh, not sure if I understood you, but you can "kill" apps from terminal by something like "sudo killall <program name>".
Hope that helps.

---

### Post by houbysoft.xf.cz on 2008-07-15
> **Kevbert said:**
> You could try
```
killall *filename*
```
where filename is the program you want to stop.

Heh you were faster :)

---

### Post by aktiwers on 2008-07-15
```
killall skype
```

You can also use the PID id. Use top to find the PID id or the app name 
```
top
```

or hit the tab key on your keyboard to autocomplete words.

---

### Post by CaseyCaseyCasey on 2008-07-16
thanks guys!

what's this top program about?  i ran it in a term but i just got a list of processes.  also, what if i have a window like 'Pictures - File Browswer' open and I want to shut that down via the CL - may I?:popcorn:

---

### Post by Dr Small on 2008-07-16
Every Applicaton has a name. The title of the window may be 'Pictures - File Browser', but the application name is probably Nautilus, the file browser.

Top is a neat little command line application that lists the top, most memory hungry applications. It should tell you the pid number of the application, and then you can run:
```
kill *pidnum*
```

Personally though, I prefer htop. Easier interface and better features :)

Dr Small

---

