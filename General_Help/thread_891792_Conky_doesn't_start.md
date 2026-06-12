---
title: "Conky doesn't start"
date: 2008-08-16
forum: General Help
---

### Post by Stan_1936 on 2008-08-16
I tried to install conky, using the instructions from their official website:

```
1. $ sudo apt-get install conky
2. $ zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

I then used ALT+F2 and entered: conky

Nothing happens at all!  I'm using Xubuntu and am running compizfusion and it shows up as being installed in Synaptic.

What am I doing wrong?

---

### Post by dexter on 2008-08-16
Open a terminal and start conky in it. If there are any errors, the will be printed in the terminal.

---

### Post by Stan_1936 on 2008-08-16
Tried it....no difference.  It said(for some reason) that conky wasn't installed.  So I installed the thing again.....STILL NOTHING!

I Quit!

---

### Post by y-lee on 2008-08-16
> Tried it....no difference. It said(for some reason) that conky wasn't installed. So I installed the thing again.....STILL NOTHING!


for some reason bash is not finding conkey. try the below and post the output here

 ```
whereis conky
```

---

### Post by Stan_1936 on 2008-08-22
I think I am having problems with this line
```
zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

I copied it exactly, and I think that the ~/. is supposed to be something else.

What does ~/. mean?  If my username is home, wouldn't it just be home.conkyrc?

---

### Post by my_key on 2008-08-22
No this means it's the ".conkyrc" file in the home directory.

BTW: the conky home page has some good sample rc files. Also, try the ubuntu an archlinux forums. Lot of nice conky configs floating around in there.

---

### Post by Stan_1936 on 2008-08-22
So can I just copy this line directly?

```
zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
```

Or do I need to change something in it?

---

### Post by my_key on 2008-08-22
Seems like a sensible command. Is the file "/usr/share/doc/conky/examples/conkyrc.sample.gz" really there?

Found some other people with a conky problem in hardy on the forums. Have you tried the suggestions over here: [http://ubuntuforums.org/showthread.php?p=4659900](http://ubuntuforums.org/showthread.php?p=4659900)

Have you tried starting conky using an rc-file of the conky site? Just put it in your home folder and run "conky -c nameofconfigfile". The way you would do it when running more than one instance of conky.

---

### Post by SkonesMickLoud on 2008-08-22
In a terminal, enter:

```
cat ~/.conkyrc
```

There should be a text file with a bunch of stuff in there.  This is the code behind what conky shows you.  IIRC, it should create this by default when it's installed.

So, you should be able to do:

```
sudo aptitude install conky && conky
```

and have it work.

By the way, the tilde (~) is an "abbreviation" of sorts for your /home.  This way if you want to get to your /home in a terminal, you'd just type "cd ~" instead of "cd /home/username"

---

