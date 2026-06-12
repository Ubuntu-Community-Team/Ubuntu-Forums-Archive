---
title: "help to install xl_cheeselooks gtk-engine"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by 220010497 on 2009-03-14
hay, well i need help, i got this theme call caramel hardy and i love it but it requiers xl_cheeselooks gtk-engine, so i down load it and follow the instructions and i opended the temal and i copy and pasted and this is what i see: 

husky@husky-laptop:~$ 
husky@husky-laptop:~$ cd to /gtk-enginesxl_cheese
bash: cd: to: No such file or directory
husky@husky-laptop:~$ ./autogen.sh --prefix=/usr --enable-animation
bash: ./autogen.sh: No such file or directory
husky@husky-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
husky@husky-laptop:~$ sudo make install
[sudo] password for husky: 
make: *** No rule to make target `install'.  Stop.
husky@husky-laptop:~$ 




the insturctions said: 
To install:
cd to /gtk-enginesxl_cheese
./autogen.sh --prefix=/usr --enable-animation
make
sudo make install



please help, my husband has no clue how to do this and hes an unbuntu lover and i'm new to it from windows

Thanks! 


<3love: cody  ):P

---

### Post by taurus on 2009-03-14
Where did you unpack the gtk-enginesxl_cheese?  Did you download it to your desktop?

What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by 220010497 on 2009-03-14
i have it to my desktop but i did the command you said and all i got was what i typed in red,  eh,  /home/husky/Desktop/gtk-enginesxl_cheese.tar.gz

---

### Post by taurus on 2009-03-14
So you have not unpacked gtk-enginesxl_cheese.tar.gz, yet.

You first need to unpack it.

```
cd ~/Desktop
tar xvzf gtk-enginesxl_cheese.tar.gz
```
That would create a new directory called gtk-enginesxl_cheese.  Now, you need to change to that new directory and build it.

```
cd gtk-enginesxl_cheese
./autogen.sh --prefix=/usr --enable-animation
make
sudo make install
```

---

### Post by 220010497 on 2009-03-14
ok i think its done but it dosent say what it normaly dose when its finnished installing something, normaly it will say: husky@husky-laptop:~$                


but it said insted this: husky@husky-laptop:~/Desktop/gtk-enginesxl_cheese$ 


dose that mean its finnished?

and if so.........THANK YOU!!! ^W^ HEHE

---

### Post by taurus on 2009-03-14
You can tell whether the process has finished successfully by looking at the last few lines.  And if everthing goes according to the plans, then you just get back your prompt, 

```
husky@husky-laptop:~/Desktop/gtk-enginesxl_cheese$ 
```
not 

```
husky@husky-laptop:~$ 
```
because you are in **husky@husky-laptop:~/Desktop/gtk-enginesxl_cheese$** when you ran those commands.

The important part is did you get any error message when you ran

```
./autogen.sh --prefix=/usr --enable-animation
```
and
```
make
```

Now, try to install that caramel hardy theme to see if it works.

---

### Post by lviggiani on 2009-07-02
Hi,
I cannot compile under Jaunty....

```
./autogen.sh --prefix=/usr --enable-animation
```

works fine

```
make
```

gives me...

```
Making all in themes
make[1]: Entering directory `/home/lviggiani/Desktop/gtk-enginesxl_cheese/themes'
Making all in xl_cheeselooks
make[2]: Entering directory `/home/lviggiani/Desktop/gtk-enginesxl_cheese/themes/xl_cheeselooks'
Making all in gtk-2.0
make[3]: Entering directory `/home/lviggiani/Desktop/gtk-enginesxl_cheese/themes/xl_cheeselooks/gtk-2.0'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lviggiani/Desktop/gtk-enginesxl_cheese/themes/xl_cheeselooks/gtk-2.0'
Making all in metacity-1
make[3]: Entering directory `/home/lviggiani/Desktop/gtk-enginesxl_cheese/themes/xl_cheeselooks/metacity-1'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/lviggiani/Desktop/gtk-enginesxl_cheese/themes/xl_cheeselooks/metacity-1'
make[3]: Entering directory `/home/lviggiani/Desktop/gtk-enginesxl_cheese/themes/xl_cheeselooks'
make[3]: *** No rule to make target `xl_cheeselooks_Orange', needed by `all-am'.  Stop.
make[3]: Leaving directory `/home/lviggiani/Desktop/gtk-enginesxl_cheese/themes/xl_cheeselooks'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/lviggiani/Desktop/gtk-enginesxl_cheese/themes/xl_cheeselooks'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/lviggiani/Desktop/gtk-enginesxl_cheese/themes'
make: *** [all-recursive] Error 1
```

Any help?
Thanks!

---

### Post by mthalis on 2009-08-19
refer this 
[http://ubuntuforums.org/showthread.php?t=778611](http://ubuntuforums.org/showthread.php?t=778611)

---

