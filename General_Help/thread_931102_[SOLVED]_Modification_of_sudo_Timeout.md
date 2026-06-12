---
title: "[SOLVED] Modification of sudo Timeout"
date: 2008-09-26
forum: General Help
---

### Post by prinny42 on 2008-09-26
I would like to change the timeout of sudo to zero, so that it always asks for my password.

Using Google, I did find [http://ubuntuforums.org/showthread.php?t=183418]("http://ubuntuforums.org/showthread.php?t=183418"), but I had trouble following its directions.

I used [http://www.washington.edu/computing/unix/vi.html]("http://www.washington.edu/computing/unix/vi.html") as a reference for how to use vi, because I have no clue how it works.  I eventually managed to add the line, but it doesn't seem to have changed anything.

In fact, I'm not sure if I haven't messed up that file in general.  Therefore, I'll show it here; please tell me if there's something wrong with it.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                                                                                                                            
~                       
```

Upon looking at it, I notice that my edits don't even seem to be there anymore.  Perhaps that's a good thing.

Also, when I bring this file up, it warns me that either another program is editing the same file or an edit session of the file crashed (I entered the file multiple times; I saved with "zz"; I twice exited with the "X" button and twice with ESC + ":q!").

I realize that I can just use "sudo -K", but I'm a bit paranoid about this and fear that I might someday forget to do so.  I'm a complete newbie to Ubuntu and all things Linux.  I just installed it on an external hard drive today.  Prior to that, my only experience with Linux is reading most of LinuxCommand.org (what convinced me to try it) and watching my cousin fail to install Red Hat when I was about eleven.

So, can someone please give me step by step instructions to set the sudo timeout to zero?

Thank you very much for any aid you might provide.

---

### Post by drs305 on 2008-09-26
First, you can use the text editor of your choice by using the following command (to use gedit in this example):
```

export EDITOR=gedit
sudo -E visudo

```

Add a line at the bottom to set timeout to 0. (Replace with your logon name):
```

Defaults:***username*** timestamp_timeout=0

```

Save as you would normally save a gedit file.

To learn about a specific command, you can type "man" and the command in a terminal window. For instance, to learn a bit about visudo, you would type:
```

man visudo

```

Welcome to ubuntu!

---

### Post by echo314 on 2008-09-26
if I remember correctly, there is an option with sudo that makes it so it prompts every time. I read through the man page a bit, and it seems to be -k, but I cant get it to work.

Maybe you can read through some of the options and try em out. 

Good luck!

EDIT: ya his way is good too :)

---

### Post by ad_267 on 2008-09-26
You could add an alias for sudo so that it uses sudo -K.

```
alias sudo="sudo -K"
```

Put that in ~/.bash_aliases and then comment out the lines in .bashrc so that the .bash_aliases file is included.

Edit: I was a bit slow, drs305's way looks a lot better.

---

### Post by prinny42 on 2008-09-27
Thank you, everyone.

When I enter that command (the one with "export (etc.)") it just returns a list of options that one can use with gksudo.  I've also looked at the manual and I don't think I saw anything that would set it so that it always prompted you.

As for aliasing, I tried aliasing "sudo -K" to both sudo/gksudo and, after that didn't work, a very simple command ("done" at the time, but "k" or something probably would have been better), but I couldn't get it to work.  I suppose I should study LinuxCommand a bit more closely...

Anyway, I think I'll adapt to just "sudo -K"ing anytime I finish using sudo.  I'm sure eventually either I'll learn enough to edit visudo or a version that allows you to edit the sudo timeout via GUI will be released.

Thanks again.

---

### Post by drs305 on 2008-09-27
prinny42,

You may not be able to combine the two commands I listed on the same line. I have revised post #4. Once you run the second command, you may see a lot of text if a previous attempt to edit the sudoers file created a sudoers.tmp.swp file. Just make sure you aren't trying to edit it simultaneously in two different windows. It will give you options, including (E) Edit, which is the one you would select.

---

### Post by prinny42 on 2008-09-27
Ah, that did the trick.  Thank you drs305.

---

