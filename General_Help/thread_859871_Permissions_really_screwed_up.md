---
title: "Permissions really screwed up"
date: 2008-07-15
forum: General Help
---

### Post by codeking on 2008-07-15
I was messing around with permissions, and ubuntu started giving me an error message each time I logged on about .dmrc didn't have the right permissions.  So I used the following commands on the ENTIRE home directory:

```

chmod 644 ./
sudo chown $USER:$USER ./

```

Now ubuntu gives me an error message about not being able to create a whole bunch of directories in home and doesn't log me in.  It said something about using failsafe sessions, but I don't know how to use those.  How can I fix this?

---

### Post by sdennie on 2008-07-15
You need to run those commands recursively:

```

sudo chown -R ${USER}:${USER} /home/${USER}
sudo chmod -R 0644 /home/${USER}

```

---

### Post by codeking on 2008-07-15
but i can't log on.  something about needing to use "failsafe sessions"

---

### Post by sdennie on 2008-07-15
In that case, hit Ctl-Alt-F1, login directly from the command line and execute those two commands.  After that, type "exit" and hit Ctl-Alt-F7 to get back to the graphical login.

---

### Post by codeking on 2008-07-15
I did that, then tried to navigate to /home/theron/ (theron is my username) but it said permission denied?  What could I be doing wrong?

---

### Post by sdennie on 2008-07-15
> **codeking said:**
> I did that, then tried to navigate to /home/theron/ (theron is my username) but it said permission denied?  What could I be doing wrong?

I don't know that should work.  Maybe try:

```

sudo chown -R theron:theron /home/theron
sudo chmod -R 0744 /home/theron
chmod 0600 /home/theron/.dmrc

```

---

### Post by codeking on 2008-07-15
Already did that (excluding the third line, because I can't even get into /home/theron/, so changing the permissions in .dmrc won't help.)

I don't see why it wouldn't of worked, I copied it down letter for letter.  Is there a way to reset the permissions or something?

**Edit:** Actually is there a way to tell the value of chmod and chown for a certain folder?

---

### Post by sdennie on 2008-07-15
Try running:

```

ls -l /home
sudo ls -l /home/theron

```

---

### Post by dfreer on 2008-07-15
Well, part of the problem might be that if a Directory does not have executable permissions, some programs won't be able to navigate the directory. I would actually run the following commands:

```
sudo chmod 755 -v $HOME    ## Makes sure home is usable.
sudo chown -Rv $USER:$USER ~/    ## Changes ownership of all files in home
find ~/ -type d -exec chmod 755 -v {} \;    ## Changes folders only to 755
find ~/ -type f -exec chmod 644 -v {} \;    ## Changes files only to 644

```

Then, go back and secure sensitive files/folders to a more restrictive setting.

---

### Post by bodhi.zazen on 2008-07-15
> **vor said:**
> You need to run those commands recursively:

```

sudo chown -R ${USER}:${USER} /home/${USER}
sudo chmod -R 0644 /home/${USER}

```

:lolflag:

There's no place like $HOME

---

### Post by codeking on 2008-07-17
Thanks for your help guys, but I just did a clean install of Ubuntu.  I didn't have any important files in home anyways.

---

### Post by carleton on 2008-07-17
> **dfreer said:**
> 

Then, go back and secure sensitive files/folders to a more restrictive setting.

Sorry for the noob question, but sensitive files/folders such as what??

---

### Post by dfreer on 2008-07-17
> **carleton said:**
> Sorry for the noob question, but sensitive files/folders such as what??

I'd have to go through my home directory, but I can give you some examples:
~/.ssh/ - Some files in here can be a security risk (if you use SSH with RSA Key to connect to a server, and if anyone gets your RSA key they can also access the server).
~/.bash_history - This file contains a list of commands you have entered into the terminal, and it should always be kept secured (you don't want people to know what programs/files you've been accessing, plus if you accidentally type your password in terminal someone can glean it from that).

Really though, it depends on what you use that user account for. If it's just an average user, there's not much that needs secured in their home folder except maybe their pr0n collection? Plus, the attacker would still need to access your machine anyways. I wouldn't worry too much about it unless you need the security or are paranoid.

---

