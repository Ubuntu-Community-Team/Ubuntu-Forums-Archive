---
title: "Accidently messed something up in terminal"
date: 2008-08-09
forum: General Help
---

### Post by goodbyecolor on 2008-08-09
I'm new to ubuntu, and I recently screwed up something in the terminal while trying to install awn.

Every time I try to get something with sudo apt-get, I get this message:

[B]E: Type 'echo' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/B]

What should I do?

---

### Post by iaculallad on 2008-08-09
> **goodbyecolor said:**
> I'm new to ubuntu, and I recently screwed up something in the terminal while trying to install awn.

Every time I try to get something with sudo apt-get, I get this message:

[B]E: Type 'echo' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/B]

What should I do?

Post whatever displays when you issue the command below on your terminal:

```
cat /etc/apt/sources.list
```

---

### Post by goodbyecolor on 2008-08-09
I still get the same thing :(
Gaahh, I'm going insane.

Is this what you wanted? I'm sorry. I didn't know what 'cat /etc/apt/sources.list' did.
> deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-security main restricted
deb-src [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-security main restricted
deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-security universe
deb-src [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-security universe
deb [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-security multiverse
deb-src [http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) hardy-security multiverse
echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main'
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main
deb [http://ppa.launchpad.net/reacocard-awn/](http://ppa.launchpad.net/reacocard-awn/) ubuntu/
deb-src [http://ppa.launchpad.net/reacocard-awn/](http://ppa.launchpad.net/reacocard-awn/) ubuntu/
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main


---

### Post by zxscooby on 2008-08-09
in the file /etc/apt/sources.list

change the line 
echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main'

to read 
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

---

### Post by iaculallad on 2008-08-09
> **goodbyecolor said:**
> I still get the same thing :(
Gaahh, I'm going insane.

That's why you have to post whatever outputs when you issue the command in your terminal. What is does is to print the file sources.list in your monitor. So you have to copy it and post it in the forum so we could help you locate the error.

---

### Post by huxterby on 2008-08-09
This line: ```
echo 'deb-src [url]http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main'
```
Should be: ```
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
```

It should have been added to the sources list with the echo command, not copied and pasted.

Once it is edited, do a ```
sudo apt-get update
``` in the terminal, or click refresh in Synaptic. Everything should be good to go after that.

Huxterby

---

### Post by goodbyecolor on 2008-08-09
Ah. I see... How exactly do I change the line?
I typed /etc/apt/sources.list into the terminal, but it says:
bash: /etc/apt/sources.list: Permission denied

---

### Post by iaculallad on 2008-08-09
> **goodbyecolor said:**
> Ah. I see... How exactly do I change the line?
I typed /etc/apt/sources.list into the terminal, but it says:
bash: /etc/apt/sources.list: Permission denied

On your terminal:

```
gksudo gedit /etc/apt/sources.list
```

and find line 56.

---

### Post by zxscooby on 2008-08-09
the file /etc/apt/sources.list
is just a list of places your computer uses to download
files from. When you added the location of AWN, a mistake was made somehow that added "echo" to the beginning of the address  and it confused apt-get.

---

### Post by goodbyecolor on 2008-08-09
YES! Everything is working now.

Thank you, everyone, for the help.

---

