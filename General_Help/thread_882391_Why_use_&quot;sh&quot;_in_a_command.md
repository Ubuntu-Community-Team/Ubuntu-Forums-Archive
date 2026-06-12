---
title: "Why use &quot;sh&quot; in a command?"
date: 2008-08-06
forum: General Help
---

### Post by dgermann on 2008-08-06
Hi--

I have a program I am having trouble getting to work. I installed it using ```
sudo ./esets.i386.deb308.bin
```

The tech support guy says I should use:
```
sudo sh ./esets.i386.deb308.bin
```

The program installs OK either way, and gives no error messages. The problem I am having occurs no matter which way I have installed it.

So I am wondering what the "sh" adds to the command.

Thanks!

---

### Post by iaculallad on 2008-08-06
Technically speaking, sh is your shell command interpreter. It is use to invoke the BASH shell or to execute .sh scripting files.

i.e:

```
sh /path/to/myScriptname.sh
```

or you could make it as an executable:

```
chmod 755 /path/to/myScriptname.sh
```

So, there will be no difference when doing:

> sudo ./esets.i386.deb308.bin

and

sudo sh ./esets.i386.deb308.bin

because it just calls your shell.

---

### Post by david_lynch on 2008-08-06
In a nutshell, to avoid the extra step of making the script executable, as the previous poster alluded.

---

### Post by dgermann on 2008-08-07
iaculallad and david_lynch--

Thank you each for your help. I had already taken the step of making the file executable, so I saw no difference. If I had not, I would have seen a difference--one way it would execute, the other it would not.

The tech guy had no way of knowing I had chmod 755 the file, so that is why he insisted on the sh.

I had thought he wanted to make sure I was using bash and not csh or tsh.

Thanks to each of you!

---

