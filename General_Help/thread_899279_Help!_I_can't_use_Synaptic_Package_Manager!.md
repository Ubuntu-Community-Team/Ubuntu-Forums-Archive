---
title: "Help! I can't use Synaptic Package Manager!"
date: 2008-08-24
forum: General Help
---

### Post by E-Cecilia on 2008-08-24
[I]I tried to install the Korean language support on Ubuntu 7.10 but the installation froze somewhere in the middle, so I had to restart the computer.

When I next started the Synaptic Package Manager I got this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and then the S. Package Manager closed.

I opened the terminal and tried to resume the broken installation but it froze again.

Is there a way that I can discard or dismiss the installation so I can use the Synaptic Package Manager again? 

Please, someone! :([/I]

---

### Post by bthoward on 2008-08-24
Open a terminal and run:

```

dpkg --configure -a

```

At least get that far then let us know what further problems are still around.

---

### Post by E-Cecilia on 2008-08-24
> **bthoward said:**
> Open a terminal and run:

```

dpkg --configure -a

```

At least get that far then let us know what further problems are still around.

[I]I did that and I got this:

Setting up language-support-ko (1:7.10+20070605) ...
Generating locales...
  ko_KR.UTF-8..

And from then on nothing "seems" to happen...

Is there a way to somehow dismiss the installation so that I can use Synpatic Manager again? :confused:
[/I]

---

### Post by fooman on 2008-08-24
follow that command up with this one:

```
sudo apt-get -f install
```

---

### Post by E-Cecilia on 2008-08-24
> **fooman said:**
> follow that command up with this one:

```
sudo apt-get -f install
```

[I]I had to close and reopen the terminal, then I typed that in. I got this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

:(
[/I]

---

### Post by bthoward on 2008-08-24
It'll probably throw and error but what happens if you try "sudo apt-get remove language-support-ko"

---

### Post by E-Cecilia on 2008-08-24
> **bthoward said:**
> It'll probably throw and error but what happens if you try "sudo apt-get remove language-support-ko"
[I]I get the same message,

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
[/I]

---

### Post by bthoward on 2008-08-24
Yea thats what I thought was going to happen.... :(  I'm at a loss...  Try running the command it tells you to run again and give it a good bit of time.  Cross your fingers...

---

### Post by E-Cecilia on 2008-08-24
> **bthoward said:**
> Yea thats what I thought was going to happen.... :(  I'm at a loss...  Try running the command it tells you to run again and give it a good bit of time.  Cross your fingers...

*Will do. Thanks a lot anyway!*

---

### Post by crgutierrez on 2008-08-24
Isn't out there anybody to help?????????????????????? I did a nex installation a few hours ago and have the very same problem. About another 3 or 4 people are in the same situation. Who is gonna check this???????

---

