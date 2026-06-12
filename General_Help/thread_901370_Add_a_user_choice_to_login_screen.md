---
title: "Add a user choice to login screen"
date: 2008-08-26
forum: General Help
---

### Post by reffu on 2008-08-26
I am the only person using my compter but idont want to use automatic login because people can still get to my computer when i am not there. However is there a way to have it automatically choose or show user accounts so i don't have to type my user name in every time. I have n problem entering a passord but id rather not have to keep entering my user name.

Thanks,

reffu

---

### Post by qstraza on 2008-08-26
Well as far as i know automatic login is not set by default.

In Kubuntu you can change this here:
System Settings -> Login manager -> Convenience

---

### Post by eggdeng on 2008-08-26
System -> Login Window Preferences -> Users tab.

---

### Post by reffu on 2008-08-26
I meant kind of more like the welcome screen in xp. or at least a drop down list. and putting my account under the include list in the user tab doesn't do what i wanted.

---

### Post by aysiu on 2008-08-26
Are these people self-professed computer illiterates or generally not curious people? If so, you can just auto login and then lock your screen.

I think you know how to set up an auto login already. To have it automatically lock your screen at login, go to System > Preferences > Sessions and add this command to the startup commands: ```
gnome-screensaver-command -l
```

If not, they can access your computer while you're away by booting into recovery mode or just booting a live CD to get at your files.

---

