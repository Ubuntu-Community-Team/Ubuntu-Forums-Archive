---
title: "Kubuntu KDE4 remix 8.04 annoying issue..."
date: 2008-10-21
forum: General Help
---

### Post by Moonfrost on 2008-10-21
I just installed Kubuntu Hardy Heron 8.04 KDE4 remix and I'm having some issues.

The problem is mostly with the "sudo" command...it works for most programs but when I try to launch "kate" (kde text editor) it says "command not found"

When I just type kate (without the sudo, which means without any root privileges) kate opens up no problem which means it IS installed and working so I don't understand. Then I tried with firefox just to test it, sudo firefox worked no problem, but then I tried another KDE specific program.

I tried "sudo konqueror" and it said command not found, then as you would have guessed I tried "konqueror" alone and it worked so I don't understand.

I tried "kdesu" also for both but still doesn't work. I'm having a problem with a wrong source I added to adept so I can't access it, luckily I already had this problem before and knew how to fix it (and it worked that way) by typing on the terminal "kdesu kate  etc/apt/sources.list and that opened the "sources.list" file with root privileges and I was able to delete the "defective" repo and then save and adept worked again without any complaints.

Now this won't work at all since I can't start kate with root privileges at all, if I type "kate  etc/apt/sources.list" it opens up the file no problem but I can't make any changes because I don't have root privileges...can anyone help? what the hell is going on? I would like help AND I would like to know WHY this is so I know for the future, thanks.

---

### Post by SuperSonic4 on 2008-10-21
KDE4 apps have a special root launch in KDE4. Try typing the below in Konsole and then kate or konqueror

```
sudo su -
```

In Mandriva it is ```
su -
```

Edit: does kwrite work still?

---

### Post by Moonfrost on 2008-10-21
> **SuperSonic4 said:**
> KDE4 apps have a special root launch in KDE4. Try typing the below in Konsole and then kate or konqueror

```
sudo su -
```

In Mandriva it is ```
su -
```

Edit: does kwrite work still?

This comes up when I type sudo su-kate
```

moonfrost@moonfrost-desktop:~$ sudo su -kate
su: invalid option -- k
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and keep
                                the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd
```

and if I type "sudo su - kate" (notice the space) this comes up

```
moonfrost@moonfrost-desktop:~$ sudo su - kate
Unknown id: kate
```

---

### Post by SuperSonic4 on 2008-10-21
That's because you don't put kate afterwards :p that goes on another line

```
sudo su -c 'kate /etc/apt/sources.list'
``` may work

---

### Post by Moonfrost on 2008-10-21
> **SuperSonic4 said:**
> That's because you don't put kate afterwards :p that goes on another line

```
sudo su -c 'kate /etc/apt/sources.list'
``` may work

That didn't work either

```
moonfrost@moonfrost-desktop:~$ sudo su -c kate /etc/apt/sources.list
Unknown id: /etc/apt/sources.list
```

EDIT: Previously I took off the ' but now I just copied the whole command and it says

```
bash: command not found
```

---

### Post by Ayuthia on 2008-10-21
The problem is that /usr/lib/kde4/bin is not included in the PATH for root.  So if you want to run konqueror or kate in sudo mode you can do the following:
```
kdesu /usr/lib/kde4/bin/kate /etc/apt/sources.list
or
kdesu /usr/lib/kde4/bin/konqueror
```

---

### Post by Moonfrost on 2008-10-21
> **Ayuthia said:**
> The problem is that /usr/lib/kde4/bin is not included in the PATH for root.  So if you want to run konqueror or kate in sudo mode you can do the following:
```
kdesu /usr/lib/kde4/bin/kate /etc/apt/sources.list
or
kdesu /usr/lib/kde4/bin/konqueror
```

Thanks a lot that helped wonders, now why wouldn't /usr/lib/kde4/bin be included in the path for root? shouldn't it be there by default as always? or is this a KDE4 problem? I'm using KDE 4.0.3 and NOT 4.1 yet since every time I try to update that something goes wrong, again thanks for your help.

---

### Post by Ayuthia on 2008-10-21
> **Moonfrost said:**
> Thanks a lot that helped wonders, now why wouldn't /usr/lib/kde4/bin be included in the path for root? shouldn't it be there by default as always? or is this a KDE4 problem? I'm using KDE 4.0.3 and NOT 4.1 yet since every time I try to update that something goes wrong, again thanks for your help.

My guess is that it is a configuration issue in Kubuntu although I could be wrong.  I have this problem in Kubuntu, but it works fine with kdemod in Arch.

For a workaround, you probably can add the path into .bashrc in /root.  I have not tried this though:
```
export PATH=/usr/lib/kde4/bin:$PATH
```It has been a while since I tried to export something.

EDIT: You will want to test this out on your user account or in the Terminal before actually adding it to .bashrc.  If it does not work, I am not for sure about what it will do for your root account.

---

