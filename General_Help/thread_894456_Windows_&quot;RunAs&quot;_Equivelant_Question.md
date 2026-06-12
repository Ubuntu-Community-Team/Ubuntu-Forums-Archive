---
title: "Windows &quot;RunAs&quot; Equivelant Question"
date: 2008-08-19
forum: General Help
---

### Post by rickyjones on 2008-08-19
Hi,

I installed Ubuntu 8.04.1 yesterday and had a thought from a usability perspective.

I needed to install a software package using a .sh script file. I browsed to the file using the file manager and double clicked it and it asked me if I wanted to Run it, Run it in terminal, or Display it. Obviously I want to run it. However it needs to run as an administrative user.

The only way to install this is via the command line.

I personally feel this is a negative mark towards Ubuntu usability.

Is there a way to configure the file manager so that when I open a file I have an option to run it as a different user? I know that I can get the functionality through sudo or su through the command line, but the point is to not use the terminal.

In Windows I can (after installing the Admin Pack from Microsoft) Shift + Right Click a file and have the "Run As" option available. I think a similar option in Ubuntu would be a great thing!

Anyone know how to accomplish this?

Thanks!

-Richard

---

### Post by loell on 2008-08-19
create a root shortcut for nautilus? so when you open the sh script it will run as root?

---

### Post by dexter.deepak on 2008-08-19
use nautilus actions instead, it will help you in other cases too.
it will get you an option in the right click menu to use it.

---

### Post by rickyjones on 2008-08-19
> **loell said:**
> create a root shortcut for nautilus? so when you open the sh script it will run as root?

When files are opened from a root-run file manager do they also open as root? How do you create this shortcut? Is it simple? Can it be done without using the terminal? 

Please note I'm looking at this from a usability and ease of use perspective as a new-ish user.

Thanks!

-Richard

---

### Post by rickyjones on 2008-08-19
> **dexter.deepak said:**
> use nautilus actions instead, it will help you in other cases too.
it will get you an option in the right click menu to use it.

I don't wish to sound dumb here but what, exactly, is "Nautilus Action"? Can you elaborate on this a little more? I've never heard of it.

Thanks,
Richard

---

### Post by lian1238 on 2008-08-19
To create a shortcut to run nautilus as root, right-click on desktop create launcher. Name it something like Root Nautilus. For command, put```
gksu nautilus
```. You should type nautilus first, then gksu, so the icon would be for nautilus instead of gksu. When you run this, you'll be prompted for root password.

---

### Post by rickyjones on 2008-08-19
> **lian1238 said:**
> To create a shortcut to run nautilus as root, right-click on desktop create launcher. Name it something like Root Nautilus. For command, put```
gksu nautilus
```. You should type nautilus first, then gksu, so the icon would be for nautilus instead of gksu. When you run this, you'll be prompted for root password.

So the launcher command should be "nautilus gksu"? Please correct me if I misunderstood.

Thanks!

-Richard

---

### Post by dexter.deepak on 2008-08-19
i am sorry i misspelled, its NAUTILUS ACTIONS,in short it is used to customize the right-click menu in ubuntu, and you can configure the default actions for a particular type of file.
this may help you use it :
[http://ubuntuforums.org/showthread.php?t=91377&page=3](http://ubuntuforums.org/showthread.php?t=91377&page=3)

---

### Post by lian1238 on 2008-08-19
No, it still should be "gksu nautilus". Just type nautilus, then go to the front (press Home) then type gksu (and space). You should end up with (gksu nautilus). The reason is that the icon will be automatically chosen for you, for the first command you type.

---

### Post by lian1238 on 2008-08-19
You can install Nautilus Actions with the command```
sudo apt-get install nautilus-actions
```I've never used it though.

---

### Post by rickyjones on 2008-08-19
> **lian1238 said:**
> No, it still should be "gksu nautilus". Just type nautilus, then go to the front (press Home) then type gksu (and space). You should end up with (gksu nautilus). The reason is that the icon will be automatically chosen for you, for the first command you type.

Ah, I misunderstood the last part of your previous post. Thanks!

---

### Post by loell on 2008-08-19
there are few ways to approach this problem like

*shortcuts - you are currently trying.

* nautilus actions? sounds interesting, havent used it

* "open with" but set it to "gksu xterm" in the properties


all of these, if you are aware, requires super user access, are you sure you want to give that power to your user?

---

### Post by rickyjones on 2008-08-19
> **loell said:**
> there are few ways to approach this problem like

*shortcuts - you are currently trying.

* nautilus actions? sounds interesting, havent used it

* "open with" but set it to "gksu xterm" in the properties


all of these, if you are aware, requires super user access, are you sure you want to give that power to your user?

The shortcut -> Nautilus as root seems to work in my test thus far.

Nautilus actions is a little more difficult to test - I can't figure out how to get it to work against launchers (like from the Applications menu).

As for giving this to my users - this is for my own personal setup - along with pointing out a usability issue (in my opinion) to my fellow Ubuntu users. I should be able to open up a program as root without having to resort to a command prompt, or logging off.

Thanks for the help everyone! I knew that something had to exist, I just didn't know what to look for. I'm hoping to test Nautilus Actions a bit more in the next few days.

-Richard

---

### Post by lian1238 on 2008-08-19
Nautilus Actions is pretty cool, now that I've tried it.

The way to configure it is using nautilus-actions-config. (System->Preferences->Nautilus Actions Configuration) or run nautilus-actions-config from terminal or Run dialog (Alt+F2).

Once opened, click Add. Label is what will appear when you right-click on a file. The Path is the command. For example, if the command-line version is ```
sudo sh /path/to/file.run
```For the path, put "gksu sh" (w/o quotes). For parameters, put "%u" for filename (w/o quotes). You can also set the Conditions, so that the right-click menu item will show only for certain files, e.g. *.run

---

### Post by oldos2er on 2008-08-19
Install the package "nautilus-gksu". Restart X, then right-click on a file and choose 'Open as Administrator.'

---

### Post by rickyjones on 2008-08-19
> **oldos2er said:**
> Install the package "nautilus-gksu". Restart X, then right-click on a file and choose 'Open as Administrator.'

Thanks! So far that one is working really well too! 

Any idea why I can't use these "Run As" options from the Gnome panels or menus?

Thanks,
Richard

---

### Post by loell on 2008-08-19
> **rickyjones said:**
> Thanks! So far that one is working really well too! 

Any idea why I can't use these "Run As" options from the Gnome panels or menus?

Thanks,
Richard

because you can just right click it, and go to properties , just add the **gksu** at the beginning of the command.

---

### Post by rickyjones on 2008-08-20
> **loell said:**
> because you can just right click it, and go to properties , just add the **gksu** at the beginning of the command.

I'd rather limit the number of extra shortcuts/launchers but this will work as well.

Thank you for the help!

Sincerely,
Richard

---

