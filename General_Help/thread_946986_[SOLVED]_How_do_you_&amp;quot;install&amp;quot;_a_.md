---
title: "[SOLVED] How do you &amp;quot;install&amp;quot; a program?  Not as noob as it sounds..."
date: 2008-10-13
forum: General Help
---

### Post by sexyclient on 2008-10-13
I'm looking to install a program that I downloaded (neroAacEnc, the nero AAC encoder) so that when I type in the program name in the terminal, it will execute.  I have it on my desktop right now, but I want to run it from the terminal without typing in the path.  How can I make this happen?

---

### Post by taladan on 2008-10-13
assuming it's in some sort of executable form (ala a shell script, a binary, etc) you have a couple of options.

```
cd ~/Desktop;./<program>
```

Or you can make life a little easier on yourself and do the following:

```
cd ~;mkdir bin;mv ~/<program> ~/bin
```

Then log out of your command line and log back in.  Type:

```
echo $PATH
```

and ensure that it shows '/home/<user>/bin' in your path.

As long as the <program> is executable ('ls -l ~/bin' & look for rwx in the first column) you can now type it from anywhere at the cli.

Tal

---

### Post by neilengineer on 2008-10-13
Also you can copy it to /usr/local/bin.

---

### Post by cariboo on 2008-10-13
THe usual place for programs that are not in the repositories is /usr/local/bin. To mv there in a terminal type:

```
sudo ~/Desktop/neroAacEnc /usr/local/bin
```

Seeing as usr/local/bin is in your path you shouldn't have to type the full path to the program to get it to run.

Jim

---

### Post by Sam on 2008-10-13
> **cariboo907 said:**
> ```
sudo [COLOR="DarkRed"]mv[/COLOR] ~/Desktop/neroAacEnc /usr/local/bin
```

Missing command.

---

### Post by sexyclient on 2008-10-13
I opted for the copy to /usr/local/bin route, hehe.  Thanks to the both of you though, neilengineer and taladan!

---

### Post by taladan on 2008-10-13
Keep in mind - if you want all users to be able to use the program, then /usr/local/bin is indeed the way to go, however if it's something that you want to be able to run without anyone else using it, or if you're just a plain user (non-sudoer) then putting it in your on ~/bin directory is the way to go.  I assumed (wrongly) that you would want to be the only user using it.  Sorry ;)

Tal

Ps - don't forget to set the thread as solved :D

---

