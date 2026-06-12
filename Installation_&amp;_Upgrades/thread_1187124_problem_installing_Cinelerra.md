---
title: "problem installing Cinelerra"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by Achilles124 on 2009-06-14
I have tried to install Cinelerra by using a deb on this page:

[http://cinelerra.org/getting_cinelerra.php]("http://cinelerra.org/getting_cinelerra.php")

It installed allright. But it is nowhere to be found. I tried this:
1. running Cinelerra from the terminal. Not to be found.
2. It is not present in the systrem tray. 
3. Desktop search with "Cinelerra". Nothing found.
4. Terminal command "find Cinelerra". Nothing found.
5. The deb-file is not to be found in computer janitor. So it is not available for cleanup.

It is there in the repositories with key. Everything is marked for downloadable except source code. 

Now I want to get rid of it, but since it wasn't installed on my system in the first place, or rather it is nowhere to be found, I cannot uninstall it?

In a way it is funny. I installed something and it is not there. Now what can I do?

---

### Post by yeats on 2009-06-14
try (in a terminal):

```
sudo apt-get remove cinelerracv
```

That should do it.

---

### Post by Achilles124 on 2009-06-14
I tried that too of course. Tried it again but now with the extension cv to the original programname. 

I get the message that the program isn't installed. And that I can delete several files with sudo apt-get autoremove. Which I did.

But the program is still in my repository and key too. I will remove the program from the repository as well as the key.

But I am baffled.

---

### Post by yeats on 2009-06-14
Do this, please:

```
dpkg -l | grep cinelerra
```

and post the output here.

---

### Post by yeats on 2009-06-14
Also, looking at your original post...

> It installed allright. But it is nowhere to be found. I tried this:
1. running Cinelerra from the terminal. Not to be found.

Did you type "_C_inelerra"?  Case matters in Linux.  Try "cinelerra."

> 2. It is not present in the systrem tray.

It's been a while since I've run Cinelerra, but I don't remember it running in the tray.

> 
3. Desktop search with "Cinelerra". Nothing found.
4. Terminal command "find Cinelerra". Nothing found.

Again - case matters.  And the find command should be:

```
[sudo] find -name cinelerra -print
```

or

```
locate cinelerra
```

would do it too.  "sudo" is necessary for the find command to be able to search certain read-protected directories.

> 5. The deb-file is not to be found in computer janitor. So it is not available for cleanup.

The "dpkg -l" command lists all the programs you have ever installed and gives their current status. (See my last post)

---

### Post by Achilles124 on 2009-06-14
Okay, ty for answering.

I tried with capital and without capital letters. The result was nada.

Find, locate, dpkg -l | grep cinelerra didn't show anything.

Just dpkg -l resulted in a long list of files. Problem was that it is that much that only the results p-z can be read in the terminal and I cannot scroll upwards till c.

I tried to install it with the code line given on the cinelerra site":
wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update

This installs the program in the repositories with a key. But that is it.

I am open for further suggestions.

---

### Post by yeats on 2009-06-14
> Just dpkg -l resulted in a long list of files. Problem was that it is that much that only the results p-z can be read in the terminal and I cannot scroll upwards till c.

Whenever that happens, you can pipe (|) your output into less, which lets you page through longer outputs:

```
dpkg -l | less
```


"q" will let you exit when you're done.

If you've followed those instructions, *some* reference to cinelerra must be in the dpkg list.

---

### Post by yeats on 2009-06-14
> I tried to install it with the code line given on the cinelerra site":
wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update

Okay - I understand now.  What you installed with this code is a package called akirad-keyring-and-mirrors, which I guess has given you what you need to download cinelerra from that specific repository.  You do not yet have cinelerra installed.  If you want to install it now, you should be able to do:

```
sudo apt-get update && sudo apt-get install cinelerracv
```

to install cinelerra.  Alternately, you can uninstall the akirad keyring package if you've just had enough :-) :

```
sudo apt-get remove akirad-keyring-and-mirrors
```

---

### Post by Achilles124 on 2009-06-15
Nope, still doesn't work with "sudo apt-get update && sudo apt-get install cinelerracv". I get the message: Couldn't find the package cinelerracv"

Tried also with cinelerra. But that didn't work either.

Now I start to think that it is not me that is making a mistake. I contacted the one responsible for this in the hope that he will fix it.

Thanks for answering my question, chrissharp123.

---

