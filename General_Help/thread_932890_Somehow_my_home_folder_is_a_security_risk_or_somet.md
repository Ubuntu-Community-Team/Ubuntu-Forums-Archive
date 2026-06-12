---
title: "Somehow my home folder is a security risk or something..."
date: 2008-09-28
forum: General Help
---

### Post by gamelord12 on 2008-09-28
I tried to share my entire home folder (under the assumption that you'd need a user name and password to access it).  Go figure, I couldn't even get to access my Ubuntu machine from a Windows machine like I wanted anyway.  However, even after changing it so that my folder is no longer shared, I get this error:

*User's $HOME/.drmc file is being ignored.  This prevents default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.*

It seems like there's an easy fix for this, but this prompt comes up every time I log in, and I want it to go away.

---

### Post by nowshining on 2008-09-28
ur problem is simple - it's a security problem - don't share ur home folder and if u read the eror u'd know what to do...

in the terminal window shown do:

sudo chmod -R username:username ~/

ur pw won't show as you type..

---

### Post by gamelord12 on 2008-09-30
My password doesn't show as I type...I can log in and everything just fine, but this error box just comes up every time.  Also, what does chmod do?

---

### Post by bobbob1016 on 2008-09-30
chmod just changes the permissions.  The line that was given to you gives your homedir the correct permissions.  He said it won't show you typing your password, so if it didn't there is nothing to worry about.

---

### Post by snova on 2008-09-30
I don't think the previous suggestion will work, but feel free to prove me wrong...

First of all, disable whatever you did to share your home directory. That's really not a good idea, try sharing individual folders instead.

Secondly, run this:

```
chmod 755 $HOME
```

To make your home folder writable only by you. To fix the second error, try this:

```
chmod 644 $HOME/.dmrc
```

---

### Post by nowshining on 2008-09-30
> **snova said:**
> I don't think the previous suggestion will work, but feel free to prove me wrong...

First of all, disable whatever you did to share your home directory. That's really not a good idea, try sharing individual folders instead.

Secondly, run this:

```
chmod 755 $HOME
```

To make your home folder writable only by you. To fix the second error, try this:

```
chmod 644 $HOME/.dmrc
```

both should do the job... :)

---

### Post by ju2wheels on 2008-09-30
> **snova said:**
> I don't think the previous suggestion will work, but feel free to prove me wrong...

First of all, disable whatever you did to share your home directory. That's really not a good idea, try sharing individual folders instead.

Secondly, run this:

```
chmod 755 $HOME
```

To make your home folder writable only by you. To fix the second error, try this:

```
chmod 644 $HOME/.dmrc
```

The previous post is a better solution. Some of the sub directories may require the same permissions, your suggestion does only the top level home folder and .dmrc, not all of the folders.

---

### Post by gamelord12 on 2008-09-30
That first suggestion doesn't work.  I put that in my terminal, replacing "username" in both instances with my username, and it says I'm not using chmod correctly.

---

### Post by lisati on 2008-09-30
> **gamelord12 said:**
> My password doesn't show as I type...I

That's normal... just type away as usual

---

### Post by gamelord12 on 2008-09-30
> **lisati said:**
> That's normal... just type away as usual

No, you misunderstood.  I wasn't concerned.  I've entered the sudo command enough times to know that my password won't show in a terminal.  I was just confused on why you pointed that out, as if it had changed since I shared my folder.  That syntax that was provided originally to recursively apply ownership back to me or whatever does not work.  How do I make it work?

---

### Post by nowshining on 2008-10-01
if snova's didn't work exactly change $HOME to /home/username/

---

### Post by davidryder on 2008-10-01
```
chmod 644 $HOME/.dmrc
```

Have you tried that?

---

### Post by snova on 2008-10-01
I didn't know this thread was still live, or I'd have checked up on it earlier.

The reason I said that the previous suggestion wouldn't work is because whoever posted it was using the command incorrectly. "chmod" changes permissions, "chown" changes owner. The command I was referring to was "chmod" being used as "chown". He was trying to make one program to another program's job. I could have been more specific, I guess...

Anyway, make sure you own your folder and all its contents:

```
sudo chown USER:USER /home/USER
```

Run it as root in case root owns a few of your files- sometimes I accidentally do that.

Obviously, you have to replace USER with your username, but that should fix the ownership problems.

---

### Post by nowshining on 2008-10-02
> **snova said:**
> I didn't know this thread was still live, or I'd have checked up on it earlier.

The reason I said that the previous suggestion wouldn't work is because whoever posted it was using the command incorrectly. "chmod" changes permissions, "chown" changes owner. The command I was referring to was "chmod" being used as "chown". He was trying to make one program to another program's job. I could have been more specific, I guess...

Anyway, make sure you own your folder and all its contents:

```
sudo chown USER:USER /home/USER
```

Run it as root in case root owns a few of your files- sometimes I accidentally do that.

Obviously, you have to replace USER with your username, but that should fix the ownership problems.

srry about that mate :)

---

### Post by gamelord12 on 2008-10-07
So now that that problem is fixed, how do I get my Windows Vista desktop to play nicely with my Ubuntu laptop?

---

