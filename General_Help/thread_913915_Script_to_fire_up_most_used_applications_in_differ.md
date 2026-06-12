---
title: "Script to fire up most used applications in different workspaces on start up?"
date: 2008-09-08
forum: General Help
---

### Post by Happibun on 2008-09-08
Hi.

Is there such a thing as a script or application that would fire up most user defined applications in different workspaces on start up? 

If there is no application, I am sure that there is some way to write such a thing, but I am very much still a new Linux user, and I really have not got to grips with user scripts yet.

I searched the forums, but I don't know if I am asking the right things or using the right terminology. I am sorry if I have overlooked something obvious, but I still don't know much about what I am doing.

What I want to do is have something that will run as I start the computer up and set up Firefox on my second workspace, and Evolution on the third.

Thanks, Jo

Update: To save some time and heartache, please read up to #6 in this thread before choosing what to do - Jo

---

### Post by justleen on 2008-09-08
the only application i know that "controls" where an app start is[ devilspie]("http://burtonini.com/blog/computers/devilspie")

the actual applications is simply from a script..
```

#!/bin/bash
firefox
evolution

```

---

### Post by Happibun on 2008-09-08
Thank you, That looks like what I was looking for :-)

---

### Post by Oldsoldier2003 on 2008-09-08
> **justleen said:**
> the only application i know that "controls" where an app start is[ devilspie]("http://burtonini.com/blog/computers/devilspie")


+1 Devilspie is definitely the way to go if you want to have apps open in separate workspaces. It would be nice if sessions would remember workspaces; but until this happens,it is the best solution I've seen so far.

---

### Post by Happibun on 2008-09-08
I have installed it and am working through the tutorial that is posted [here]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/"). That should keep me busy for the evening :-)

Update - VI editor info and tutorial [here]("http://www.eng.hawaii.edu/Tutor/vi.html").

---

### Post by Happibun on 2008-09-09
Hello again gentlemen,

I'm writing again because I've been on a long learning curve, and it might help someone else if I record my findings here. I hope that's OK.

I can't say that I had a particularly easy evening of it last night. Though I managed to find and install devilspie through the package manager OK, writing scripts for it involved my first encounter with the VI editor, and I am afraid that it was an unnerving experience even with the tutorial. To be fair, if I had the time to sit and go through it all properly, I expect that I would not be so confused, but I didn't have the time. All the same I managed to get in and out of it ok, write and save something (3 times - one each for Firefox, Evolution and Debug). Then I had a look through the forums again to see how I could actually make it work. I discovered that instead of set_workspace, I should have used set_viewport because I have compiz working on my desktop. I also found too late, that there is somewhere a GUI for devilspie called gdevilspie, but I would have had to install from a tar.gz - which frightens me because I still don't know what I am doing.

I had another search because I was trying to figure out how to edit saved and closed files from VIM, and discovered this -

>                                   **Re: Devilspie!!**             
                                                                You don't need to use devilspie if you're running Compiz. If you haven't already, install the compizconfig-settings-manager package by typing "sudo apt-get install compizconfig-settings-manager" in the terminal. Now go to System->Preferences->Advanced Desktop Effects Settings and click the Place Windows plugin in the Window Management section. Click the Fixed Window Placement tab, and you'll see a section called "Windows with fixed viewport". Click the New button, and that will open a new window with placement options. 

At this point, if you're familiar with devilspie you should be able to figure things out on your own. Click the "+" button, which will open another window which lets you select the program you want to place. If you open the application you want to place, then click the "Grab" button and click somewhere on the application window, it will add the value for whatever type you specify. Click the Add button, which will take you back to the first window. Select the workspace where you want to place the application (if you're using a desktop cube, you would enter an X value from 0 to 3), and click close. Now when you open the application, it will automatically open on that workspace.

In my opinion, it's considerably simpler and easier to manage than writing devilspie scripts...
by **[mb_webguy]("http://ubuntuforums.org/member.php?u=475703")** on this [thread]("http://ubuntuforums.org/showthread.php?t=903186").

What is more, there is a function under System > Preferences > Sessions (configure your sessions) which pulls up a three tab box where you can specify what programs automatically run on start up, and on the third tab, remember what programs are running when you log out.

So, because I thought it had messed up devilspie beyond useful function, I uninstalled it. Then I went in to the Compiz menus and allocated a window to Firefox and Evolution. Then I used Session preferences to boot those programs on start up.

I know it is probably not as far reaching as devilspie, but it works for me. Yes, I am sure that I could do more with devilspie too, and that aparently KDE has this functionality built in in a handy GUI, but I am still very new to this, and most of the time don't even know where to begin to start searching.

I can see now that it would have been relevant to tell you that I use Compiz, but yesterday, I didn't know. Sorry.  :oops:

It did help having the name Devilspie to search, because it bought up a lot more information, and without it, I would not have discovered the Compiz work round, but then again, I'd never heard of it before yesterday. Nor VIM come to think of it.

Such is life.

---

