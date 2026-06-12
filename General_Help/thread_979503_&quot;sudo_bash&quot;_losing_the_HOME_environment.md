---
title: "&quot;sudo bash&quot; losing the HOME environment"
date: 2008-11-12
forum: General Help
---

### Post by freemant on 2008-11-12
Hi,

Any idea why running "sudo bash" will lose the HOME environment variable:

kent@cladms003:~$ echo $HOME
/home/kent
kent@cladms003:~$ printenv|wc -l
17
kent@cladms003:~$ sudo bash
root@cladms003:/home/kent# echo $HOME

root@cladms003:/home/kent# printenv|wc -l
16

---

### Post by jpkotta on 2008-11-12
That is not the recommended way to do that.  Use -s or -H, depending on what you want to do.
```
sudo -s
```

This is like logging in as root.
```
sudo -i
```

Similar to -i, but preserves some of your environment.
```
sudo su
```

---

### Post by xX@v@Xx on 2011-10-24
Any of thoses switch solves my problem.
I got a emacsserver running as a ubuntu normal user that is working fine.
When I switch under sudo the path to the emacsserver is lost:

For example  
sudo emacsclient /etc/udev/rules.d/51-android.rules
returns
emacsclient: can't find socket; have you started the server?
To start the server in Emacs, type "M-x server-start".
emacsclient: No socket or alternate editor.  Please use:

    --socket-name
    --server-file      (or environment variable EMACS_SERVER_FILE)
    --alternate-editor (or environment variable ALTERNATE_EDITOR)

I am not really sure but it seems that the behaviour was dfifferent with old ubuntu releases. I experience this from 11.04 at least.
What the work-around here ?

Thks

---

### Post by xX@v@Xx on 2011-10-24
Also this doesn't work as it is said into the manual 

sudo -u <username> emacsclient ....  

the file is effectively loaded into the emacs server but still remains read-only

so any help welcome...

---

