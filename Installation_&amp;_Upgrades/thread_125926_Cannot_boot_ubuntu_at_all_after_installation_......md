---
title: "Cannot boot ubuntu at all after installation ............"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by sahibvirk on 2006-02-05
I use the Acronis OS-Loader to boot all the operating systems. I wanna uae it as my main boot loader. I installed ubuntu and put the LILO boot loader in the new ubuntu partition. Acronis detected the OS. When I click on its icon, it LILO boot loader is initiated. It starts loading ubuntu. But now is where the problem starts. Certain kinds of problems start showing up. These 2 are some of them:-
1. Cannot find sbin/init
2. /bin/sh :cant access tty; job control turned off

I repeated the installation twice, but faced the same problem.
Please tell me what to do.

And yeah, I dont want any other boot loader in my MBR. Because I bought the Acronis Disk Director Suite for a very costly price. And I use it to boot many other OS's(Windows xp[2-versions], FreeBSD, Fedora).

Any help will be appreciated.

Thanks in advance..............................................


YAO-YAO-YAO
KEEP SEEDING
KEEP SHARING
AS YOU HELP
SO SHALL YOOU REEP

---

### Post by taurus on 2006-02-05
Maybe there is something wrong, typo, in your /etc/lilo.conf so if you don't mind, a copy of it would be nice.  Just so you know, GRUB which is free as in free beer can handle all those OSes...

---

### Post by sahibvirk on 2006-02-06
Well guess what ??????????????????

There is no lilo.conf inside the /etc/ :-

Well let me tell you what actually happens when the ubuntu tries to boot. First the system shows some errors like these :-
1. Cannot find sbin/init
2. /bin/sh :cant access tty; job control turned off
Then it by itself logins as root into the shell. No XWindows, no graphics, no nothing......................................

Please help me. I have the original ubuntu installation CD's, so there cant be any problem with the installattion media. I just cannot understand whats going wrong here.

The only problem or error that I faced during the installation was : "Cannot partition for ubuntu maybe because this disk has too many primary partitions". But when I clicked on continue it partitions the disks perfectly and installed ubuntu.
Can this be the cause.
Please help..................................................

---

### Post by sahibvirk on 2006-02-07
I even deleted one primary partition and re-installed ubuntu. And this time there was no error during partitioning. But it did not work.

I still have the same problem.


Common somebody has got to help me !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!11

---

### Post by pnael on 2006-02-07
The acronis software seems to be able to hide partition from the OS. It could be that when you install from the CD and when you boot from Acronis the partition naming is somewhat changed. 


Please provide the output of :
mount
cat /etc/fstab
fdisk -l /dev/hda

when you get the prompt of Ubuntu.

---

### Post by sahibvirk on 2006-02-09
1. both the commands are nopt working.

2. Stop blaming Acronis OS-Loader. It's a great software. Works perfectly with any other OS in the whole damn world. That is why I spent so much money on it..

3.All of you suck.

4. You idiots dont even reply.

5. I will install freebsd instead.

6. Worse support I have ever seen.

7. You can delete this thread. I will throw away the stupid ubuntu CD's.

---

### Post by kingsidy on 2006-02-09
#^*$ing acronis idiot. shove it.

---

### Post by sahibvirk on 2006-02-10
If you cannot solve an OS problem then you dont shove it.

Acronis does not change any partition label. I havee checked that already. I am already multi-booting two WindowsXP, fedora core-4,& freebsd unix with it. I never had any problems with it. It's the costliest and the best os-loader.

Solve this problem if you can, or dont praise it so much.

If things go like this, ubuntu can never be an alternative for windows in a 100-years.

---

### Post by Teroedni on 2006-02-10
[QUOTE=sahibvirk]If you cannot solve an OS problem then you dont shove it.

Acronis does not change any partition label. I havee checked that already. I am already multi-booting two WindowsXP, fedora core-4,& freebsd unix with it. I never had any problems with it. It's the costliest and the best os-loader.

Solve this problem if you can, or dont praise it so much.

If things go like this, ubuntu can never be an alternative for windows in a 100-years.[/QUOTE]

It is already an alternative;)

Why do you get so mad?
were not paid to help you, we do it of our own will

i see you got a partitopn problem
Do you use ubuntus partition tool
If yes maybe you should try another partition tool and then point ubuntu to the newly created partition;)

---

### Post by sahibvirk on 2006-02-10
FINE .......................

I'will give it a try .....................................
I have tried everything else anyways .........................

---

### Post by sahibvirk on 2006-02-10
[center]**[size="7"]TRIED IT[/size]**

**[size="7"]DIDNT WORK[/size]**[/center]

---

### Post by sahibvirk on 2006-02-10
[B][COLOR="Red"]NEED HELP FAST !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1



PLEASE !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!![/COLOR][/B]

---

### Post by sahibvirk on 2006-02-12
Common people ......................


SOMEBODY HAS GOTTA HELP ME ........................

IS THERE NOBODY HERE SMART ENOUGH ................................

---

### Post by daFoos on 2006-03-11
well that's great

---

### Post by Resurrection on 2006-03-11
Just ignore sahibvirk.  Not because the problem is unsolvable but because he/she is acting like a jerk.  

Time to grow up.  Welcome to the real world, where no matter how much you pout and throw a tantrum, people won't help you if you piss them off.  Good luck with your problem, hope you solve it on your own, because you don't deserve the help of a great community like this.

---

