---
title: "jaunty install keyboard broke"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by tim2xu on 2009-06-29
Hi 
I was doing a fresh install from the alternate cd and when I got to the part of the install where you create the new user and password my keyboard wouldn't type any thing no matter what I tried, so I skipped that part and finished the install. My problem is now I have a login prompt and no way to get in! is there any way to fix this from the command line? 
I don't want to start over fresh again because I'll just get stuck again when it comes time to type anything.
Thanks

---

### Post by QIII on 2009-06-29
I'm not being cute, so please bear with me.

My stupid dog chases tennis balls under my desk quite often.  Invariably, my keyboard stops working.  He tramples all over the cables and something gets pulled off the back of one of my machines.

Before you get too worried, please shut the machine down, check your connection and restart.  

Let us know if that doesn't take care of it.

The next thing we'll try is how you set up your keyboard during the install.

---

### Post by tim2xu on 2009-06-30
QIII
I'm positive the keybaord works, it's only during the install process that it screws up. When it asks you to type in the full name of the user, it just sits there. all the tab, enter, arrow, and other keys work. It seems like a bug with the installer.

---

### Post by cariboo on 2009-06-30
You could start in recovery mode, once at the menu select drop to root prompt. Once at the prompt type:

```
useradd -m <username>
```

This will create your home directory, next you need to set a password:

```
passwd <username>
```

Once you have created the user, at the prompt type:

```
exit
```

Then select Resume from the menu. This should start gdm and allow you to login.

---

### Post by QIII on 2009-06-30
Edit -- cariboo may have it.  My understanding was that your keyboard wouldn't work at install, either.

Some time before that it should ask you to set keyboard configuration.  I think the default is US.  Did you try typing anything there to test it?

Is it a USB or wireless keyboard?

---

### Post by tim2xu on 2009-07-01
> **cariboo907 said:**
> You could start in recovery mode, once at the menu select drop to root prompt. Once at the prompt type:

```
useradd -m <username>
```

This will create your home directory, next you need to set a password:

```
passwd <username>
```

Once you have created the user, at the prompt type:

```
exit
```

Then select Resume from the menu. This should start gdm and allow you to login.
cariboo
I took your suggestion and used recovery mode to create a user so Ican log in now. The problem now is that Ihave no administrator rights. any suggestions? I appriciate the help. Thanks

---

### Post by tim2xu on 2009-07-01
I was able to get admin rights in recovery mode with: 
adduser <myname> admin.
However now when I try to use the update manager it throws up this message:

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '50331684' '-o' 'Synaptic::closeZvt=true' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpu1iff0' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

Any ideas?

---

