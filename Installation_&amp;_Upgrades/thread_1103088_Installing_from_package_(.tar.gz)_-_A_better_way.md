---
title: "Installing from package (.tar.gz) - A better way?"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by Brandon! on 2009-03-22
So I've install Ubuntu for the third time now and each time I'm determined to really understand it and be fluid in it.  I don't see it replacing my main PC any time soon, but I do really like having it as my secondary machine.  I spent all day yesterday installing LAMP and really had fun configuring and learning how to do it all.  That being said, the reason I always seem to run back to Windows is that what should be a simple task seems overly complicated on Linux.  Since I'm determined for this to work this time, I want to see if maybe the complications are my fault and if I'm doing more than I have to.

Today's frustration was to install CrashPlan ([http://www.crashplan.com/](http://www.crashplan.com/)).  I have been using this on my two Windows machines for awhile and the installation was very simple.  Download exe, right click open, hit next until I'm done (basically).  Very dummy friendly.

Now I went to install it with Ubuntu, and I had to stumble through it.  Granted this is my first time installing something outside of Synaptic or aptitude, but I had hoped it would be a lot easier.  First, I downloaded the .tar.gz., said Open with [Archive Manager].  Download finished and I got "... could not be opened, because the associated helper application does not exist."  Alright, I guess I'll try and save it to my downloads directory and go from there.  Re-downloaded (note, trying to do "retry" in Firefox gave me a permissions error, so I had to find the download page again), and opened the file.  I see the INSTALL readme which tells me the command line to run.  If I double click on the install.sh, I see the install source code (not what I wanted at all).  I figure I have to bite the bullet and use terminal, so I open an instance.  Then I have to cd to wherever it was downloaded (~/Downloads), use tar to extract it.  cd into the dir it just extracted to and run install.sh.  Nope, I have to use ./install.sh... Now I'm prompted a bunch of times: first for sudo privs, then I have to more through the EULA and then verify all of these paths that I'm not even sure about.

Luckily, I was able to install by braile with no problems, but I'm not thrilled about how many steps (and how much typing) I had to go through just to install a *simple* app.  If Ubuntu wants to get the consumer to use this OS, something has change.  THere's no way I will ever be able to teach my mom (forget about my Grandma!) how to use tar and understand how to install a program.

I'm hoping that there are some steps I can cut out. Perhaps a way to run a .sh from the GUI?  Also, is there a way to say "open terminal at this directory"?  Either of those would save me some trouble and be a better start maybe.  I'm also not sure why Firefox didn't find the Archive Manager.  If someone has input on that, I would appreciate that too.

---

### Post by oldos2er on 2009-03-22
If you're using Gnome, install the package nautilus-open-terminal. It will add an 'Open in terminal' option to Nautilus' right-click menu.

 Odd that Archive Manager didn't work; it should be able to handle tar.gz files "out of the box."

---

### Post by Brandon! on 2009-03-22
'ppreciate that.  I knew that I had seem the "Open terminal here" once before, but I didn't remember having to isntall something for it.

---

### Post by bubwitmaingay on 2009-03-22
I think you can use the "alien" command at the terminal. It converts tar.gz to .deb, but I have a problem running the application though after installing the converted tar.gz file to debian file. I think you should type a command "sudo cache" or something to make the application running.

Open the terminal and type "man alien", it sure will give you a manual on the alien command. I think alien is a better way to install tar.gz converting it to .deb. 8)

---

### Post by oldos2er on 2009-03-23
alien is for converting RPMs to deb, I don't believe it will work on source code.

---

