---
title: "installing a tar.gz file"
date: 2008-09-01
forum: General Help
---

### Post by jaland on 2008-09-01
I am very new to unix, but I was trying to install a new file on my computer. I opened the terminal screen and typed sudo tar xfvz hack-1.0.3.tar.gz to unpack it which seemed to work because this game up

./hack-1.0.3/
./hack-1.0.3/Makefile
./hack-1.0.3/Original_READ_ME
./hack-1.0.3/READ_ME
./hack-1.0.3/alloc.c
./hack-1.0.3/config.h
./hack-1.0.3/data
./hack-1.0.3/date.h
./hack-1.0.3/def.edog.h
./hack-1.0.3/def.eshk.h
./hack-1.0.3/def.flag.h
./hack-1.0.3/def.func_tab.h
./hack-1.0.3/def.gen.h
./hack-1.0.3/def.gold.h
./hack-1.0.3/def.mkroom.h
./hack-1.0.3/def.monst.h
./hack-1.0.3/def.obj.h
./hack-1.0.3/def.objclass.h
./hack-1.0.3/def.objects.h
./hack-1.0.3/def.permonst.h
./hack-1.0.3/def.rm.h
./hack-1.0.3/def.trap.h
./hack-1.0.3/def.wseg.h
./hack-1.0.3/hack.6
./hack-1.0.3/hack.Decl.c
./hack-1.0.3/hack.apply.c
./hack-1.0.3/hack.bones.c
./hack-1.0.3/hack.c
./hack-1.0.3/hack.cmd.c
./hack-1.0.3/hack.do.c
./hack-1.0.3/hack.do_name.c
./hack-1.0.3/hack.do_wear.c
./hack-1.0.3/hack.dog.c
./hack-1.0.3/hack.eat.c
./hack-1.0.3/hack.end.c
./hack-1.0.3/hack.engrave.c
./hack-1.0.3/hack.fight.c
./hack-1.0.3/hack.h
./hack-1.0.3/hack.invent.c
./hack-1.0.3/hack.ioctl.c
./hack-1.0.3/hack.lev.c
./hack-1.0.3/hack.main.c
./hack-1.0.3/hack.makemon.c
./hack-1.0.3/hack.mfndpos.h
./hack-1.0.3/hack.mhitu.c
./hack-1.0.3/hack.mklev.c
./hack-1.0.3/hack.mkmaze.c
./hack-1.0.3/hack.mkobj.c
./hack-1.0.3/hack.mkshop.c
./hack-1.0.3/hack.mon.c
./hack-1.0.3/hack.monst.c
./hack-1.0.3/hack.o_init.c
./hack-1.0.3/hack.objnam.c
./hack-1.0.3/hack.onames.h
./hack-1.0.3/hack.options.c
./hack-1.0.3/hack.pager.c
./hack-1.0.3/hack.potion.c
./hack-1.0.3/hack.pri.c
./hack-1.0.3/hack.read.c
./hack-1.0.3/hack.rip.c
./hack-1.0.3/hack.rumors.c
./hack-1.0.3/hack.save.c
./hack-1.0.3/hack.search.c
./hack-1.0.3/hack.sh
./hack-1.0.3/hack.shk.c
./hack-1.0.3/hack.shknam.c
./hack-1.0.3/hack.steal.c
./hack-1.0.3/hack.termcap.c
./hack-1.0.3/hack.timeout.c
./hack-1.0.3/hack.topl.c
./hack-1.0.3/hack.track.c
./hack-1.0.3/hack.trap.c
./hack-1.0.3/hack.tty.c
./hack-1.0.3/hack.u_init.c
./hack-1.0.3/hack.unix.c
./hack-1.0.3/hack.vault.c
./hack-1.0.3/hack.version.c
./hack-1.0.3/hack.wield.c
./hack-1.0.3/hack.wizard.c
./hack-1.0.3/hack.worm.c
./hack-1.0.3/hack.worn.c
./hack-1.0.3/hack.zap.c
./hack-1.0.3/help
./hack-1.0.3/hh
./hack-1.0.3/makedefs.c
./hack-1.0.3/rnd.c
./hack-1.0.3/rumors
./hack-1.0.3/COPYRIGHT
./hack-1.0.3/COPYRIGHT-JF
 BUT then i typed ./hack-1.0.3/READ_ME but i got a permission denyied. What should i do now like i said i am very new to the system.

---

### Post by cszikszoy on 2008-09-01
Usually you would just go to the directory where everything was unpacked and type:

```
./configure
sudo ./make
sudo ./make install
```

Mind if I ask what it is you are trying to install?

---

### Post by coffeecat on 2008-09-01
> **jaland said:**
> I am very new to unix, but I was trying to install a new file on my computer. I opened the terminal screen and typed sudo tar xfvz hack-1.0.3.tar.gz to unpack it which seemed to work because this game up

<snip>


BUT then i typed ./hack-1.0.3/READ_ME but i got a permission denyied. What should i do now like i said i am very new to the system.

You went wrong when you used 'sudo' to untar the file. This would have made everything untarred owned by root which is why you are getting the permission denied message. In future (so long as you are in your home folder), do the tar command without the sudo. You have to sudo the make install bit later, which will give you root privileges for the install - this is the only time you need root privileges. But for now, do:

```
sudo chown -R *yourusername*: hack-1.0.3
```That should make the hack folder and everything in it owned by you. Substitute your user name for *yourusername* and don't forget the trailing colon.

Now simply navigate to inside the hack-1.0.3 folder with Nautilus (the file browser) and double-click on the readme file. It will open in a text editor where you can read it.

> **cszikszoy said:**
> Mind if I ask what it is you are trying to install?

I was wondering the same. The word 'hack' made me wonder whether it was dodgy. But I found [this]("http://nethack.wikia.com/wiki/Hack_1.0.3"). It seems to be a game and it's not in the Ubuntu repositories. **jaland**, is this what you are trying to install?

---

### Post by jaland on 2008-09-01
Lol yea sorry probably should have mentioned that. It is a game one of my friends recommended. Don't worry even if it was a hacking tool i could not use it; heck I can not even install it lol.

---

### Post by cszikszoy on 2008-09-01
Did you ever get it installed with the advice from the previous posts?

---

### Post by jaland on 2008-09-02
jaland@JamiesComputer:~$ sudo chown -R jaland: hack-1.0.3
[sudo] password for jaland: 
jaland@JamiesComputer:~$ ./hack-1.0.3/READ_ME
bash: ./hack-1.0.3/READ_ME: Permission denied
 nope still doing this

---

### Post by cszikszoy on 2008-09-02
**edit**

Sorry, the advice below is better.

---

### Post by coffeecat on 2008-09-02
> **jaland said:**
> jaland@JamiesComputer:~$ ./hack-1.0.3/READ_ME
bash: ./hack-1.0.3/READ_ME: Permission denied
 nope still doing this

You can't read a text file by trying to run it from a bash prompt. If you are 'in' the directory that contains the text file you get a "bash: READ_ME: command not found" error. Bizarrely, if it's in a subordinate folder you get the permission denied error instead (just as you did), even though you've chown'd ownership.

Ho hum. :sigh: Did you read this?

> **coffeecat said:**
> Now simply navigate to inside the hack-1.0.3 folder with Nautilus (the file browser) and double-click on the readme file. It will open in a text editor where you can read it.

---

### Post by Xiong Chiamiov on 2008-09-02
The reason you're getting a Permission denied error is because you're trying to execute a non-executable file.  To view the contents of a file, use cat, less, gedit, or somesuch:
```

less ./hack-1.0.3/READ_ME

```

Beyond that, the instructions cszikszoy gave above are correct for compiling something from source (which is what you're trying to do).  The only addition I'd add is to use, uh, checkinstall instead of make install.  There is a most excellent guide on installing things over [here]("http://monkeyblog.org/ubuntu/installing/"), although the site currently is down, so you'll have to take a look at [Google's cache]("http://209.85.141.104/search?q=cache:IfbspYjsGWIJ:www.monkeyblog.org/ubuntu/installing.html+how+to+install+anything+ubuntu&hl=en&ct=clnk&cd=1&gl=us").

---

### Post by coffeecat on 2008-09-02
> **cszikszoy said:**
> I would say the best thing to do is just delete the files, and try again.

But this time, don't use sudo to untar them, so that they are owned by your user.

Delete them with:
```
rm -r ./hack-1.0.3/
```

I was thinking along those lines, but it's probably not necessary. I've done a little experiment. Even if you own the readme file and it's in a separate directory from where you are in the terminal, you get the permission denied error. It must be a bug. And, anyway, the OP shouldn't be trying to run a text file from the terminal. See my previous post for more details.

---

### Post by forger on 2008-09-02
It's in the Ubuntu repositories, package: **bsdgames**
> Description: a collection of classic textual unix games
 This is a collection of some of the text-based games and amusements that have
 been enjoyed for decades on unix systems.
 .
 Includes these programs: adventure, arithmetic, atc, backgammon, battlestar,
 bcd, boggle, caesar, canfield, countmail, cribbage, dab, go-fish, gomoku,
[COLOR="Red"]** hack**[/COLOR], hangman, hunt, mille, monop, morse, number, pig, phantasia, pom, ppt,
 primes, quiz, random, rain, robots, sail, snake, tetris, trek, wargames,
 worm, worms, wump, wtf


Execute this in a terminal:
```
sudo apt-get install bsdgames
/usr/games/hack

```

---

### Post by Xiong Chiamiov on 2008-09-02
> **coffeecat said:**
> I was thinking along those lines, but it's probably not necessary. I've done a little experiment. Even if you own the readme file and it's in a separate directory from where you are in the terminal, you get the permission denied error. It must be a bug. And, anyway, the OP shouldn't be trying to run a text file from the terminal. See my previous post for more details.
Reading text files in bash is perfectly valid; you cannot *execute* them, however; they must be opened with another program, eg. less, cat, nano, vim, etc.

---

### Post by cszikszoy on 2008-09-02
> **coffeecat said:**
> I was thinking along those lines, but it's probably not necessary. I've done a little experiment. Even if you own the readme file and it's in a separate directory from where you are in the terminal, you get the permission denied error. It must be a bug. And, anyway, the OP shouldn't be trying to run a text file from the terminal. See my previous post for more details.

That's why I retracted my statement :)

> **forger said:**
> It's in the Ubuntu repositories, package: **bsdgames**

Execute this in a terminal:
```
sudo apt-get install bsdgames
/usr/games/hack

```

Probably your best bet.  I would highly suggest that the you (OP) do this instead of trying to install from source.

---

### Post by jaland on 2008-09-02
ok thanks guys, sorry for the confusion i appreciate it.

---

