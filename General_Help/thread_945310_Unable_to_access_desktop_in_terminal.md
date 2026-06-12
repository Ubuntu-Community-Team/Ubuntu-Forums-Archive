---
title: "Unable to access desktop in terminal"
date: 2008-10-12
forum: General Help
---

### Post by Fatfool on 2008-10-12
```
jeffery@Roomcomp:~$ $cd ~/Desktop
bash: /home/jeffery/Desktop: is a directory
jeffery@Roomcomp:~$ cd /home
jeffery@Roomcomp:/home$ ls
jeffery
jeffery@Roomcomp:/home$ cd /jeffery
bash: cd: /jeffery: No such file or directory
jeffery@Roomcomp:/home$ cd /jeffery
bash: cd: /jeffery: No such file or directory
jeffery@Roomcomp:/home$ ls
jeffery
jeffery@Roomcomp:/home$ cd /jeffery
bash: cd: /jeffery: No such file or directory
jeffery@Roomcomp:/home$ 

```

hmm yes, I have problem here... I can't access the home folder. I won't be able to reply for a week though so any suggestions?
I've just installed Alien to convert .rpm to .deb btw.

edit: fixed. A restart fixed this
edit 2: its back again. whats wrong arg!!

---

### Post by detroit/zero on 2008-10-12
> **Fatfool said:**
> ```
jeffery@Roomcomp:~$ $cd ~/Desktop
bash: /home/jeffery/Desktop: is a directory
jeffery@Roomcomp:~$ cd /home
jeffery@Roomcomp:/home$ ls
jeffery
jeffery@Roomcomp:/home$ cd /jeffery
bash: cd: /jeffery: No such file or directory
jeffery@Roomcomp:/home$ cd /jeffery
bash: cd: /jeffery: No such file or directory
jeffery@Roomcomp:/home$ ls
jeffery
jeffery@Roomcomp:/home$ cd /jeffery
bash: cd: /jeffery: No such file or directory
jeffery@Roomcomp:/home$ 

```hmm yes, I have problem here... I can't access the home folder. I won't be able to reply for a week though so any suggestions?
I've just installed Alien to convert .rpm to .deb btw.

edit: fixed. A restart fixed this
edit 2: its back again. whats wrong arg!!
I'm not sure why **cd ~/Desktop** doesn't work, but in your commands you're typing **cd /jeffery**, so it's looking for a folder named jeffery in your root directory, which is right where that folder isn't.

When the terminal opens, your command prompt states the current directory.```
zero@zero-laptop:[COLOR=Red]~[/COLOR]$
``` ```
zero@zero-laptop:[COLOR=Red]~[/COLOR]$ cd Desktop
zero@zero-laptop:[COLOR=Red]~/Desktop[/COLOR]$ 
```If you need to see it again, the comand```
pwd
```will show you again:```
zero@zero-laptop:~$ pwd
/home/zero
zero@zero-laptop:~$ 
``````
zero@zero-laptop:[COLOR=Red]~/Desktop[/COLOR]$ pwd
/home/zero/Desktop
zero@zero-laptop:[COLOR=Red]~/Desktop[/COLOR]$
```Switching to your desktop from your home directory should be as easy as:```
zero@zero-laptop:~$ cd Desktop
zero@zero-laptop:~/Desktop$ pwd
/home/zero/Desktop
zero@zero-laptop:~/Desktop$ 
``` Since *Desktop* is a folder in your home directory, it isn't necessary to preceed it with the **~/**, provided you're going there *from* your home directory.

The strange thing is, typing the absolute path (i.e., **~/Desktop** or **/home/jeffery/Desktop**) should put you in your desktop folder from anywhere you may be.

Remember your filesystem structure when typing out file paths in the terminal.
Example:```
/home/jeffery/somefile.txt
```The very first **/** out from is the name for your root directory. Typing **cd /** from anywhere inside your system will take you back to your root directory which should look a lot like this:```
zero@zero-laptop:~/Desktop$ cd /
zero@zero-laptop:/$ ls
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
zero@zero-laptop:/$ 
```So when you're typing **cd /home/jeffery**, you're telling the computer to take you to a folder named jeffery which is a subfolder of home, which resides in your root directory - i.e., root > home > jeffery 

The symbol **~** is shorthand for that exact position in your filesystem.

~ = /home/yourname

What happened is when you did:```
jeffery@Roomcomp:~$ cd /home
jeffery@Roomcomp:/home$ ls
jeffery
jeffery@Roomcomp:/home$ cd /jeffery
bash: cd: /jeffery: No such file or directory
```You went from your home directory to one level higher. You went from **/home/jeffery** to **/home**, and then were trying to cd to a directory named **/jeffery**, which I presume does not exist (if your root directory looks anything like mine up there).

Just like I showed you that typing cd / anywhere will always take you to your root folder, typing **cd /home/jeffery** or **cd ~** will always take you to *your* home folder, rather than the home directory (**/home**).  

Hope I helped somehow.

---

### Post by Fatfool on 2008-10-12
ah ok. thanks for explaining. I managed to get to the desktop with it :D.

---

