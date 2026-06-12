---
title: "Vaio webcam Ricoh - r5u87x for ubuntu 20.04?"
date: 2020-05-20
forum: Hardware
---

### Post by rpessoa on 2020-05-20
I found some old post here on how to install the driver for Ricoh webcams.

I have an old Vaio that, unfortunately, has this hardware.

I followed the steps from this site: [https://launchpad.net/~r5u87x-loader/+archive/ubuntu/ppa](https://launchpad.net/~r5u87x-loader/+archive/ubuntu/ppa)

But it didn't work. I get the following error message when I do a "sudo apt install r5u87x"

```

The following packages have unmet dependencies:
r5u87x: Depends: module-init-tools but it is not installable
E: Unable to correct problems, you have held broken packages.

```

I tried to install "module-init-tools" but it is missing or is obsoleted.

Any idea how to make this Ricoh webcam from a Sony Vaio working under Ubuntu 20.04?

Thanks! :)

---

### Post by bharan1 on 2020-05-28
[FONT=arial]
I had the same issue on my sony vaio VGN CR590 after installing Ubuntu 20.04. I managed to fix (after a day's struggle) it by compiling and installing the r5u87x package from the[ source code]("https://bitbucket.org/ahixon/r5u87x/src/default/") itself.

The following steps worked for me.

1. It is beneficial to point to the "main server" in 'software and updates' tool in order to download any packages from. Install any pending updates.

2. Follow the below steps
[/FONT]```
[FONT=-apple-system]
sudo apt-get update -y
sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial 
hg clone [/FONT][http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)[FONT=-apple-system] 
cd r5u87x 
make 
sudo make install 
sudo r5u87x-loader --reload
[/FONT]
```[FONT=-apple-system]
[FONT=arial]Now you can open cam tools like cheese or guvcview and see the camera working. [/FONT][/FONT][FONT=arial];)[/FONT][COLOR=#172B4D][FONT=-apple-system]
[/FONT][/COLOR]

---

### Post by rpessoa on 2020-05-28
> **bharan1 said:**
> [FONT=arial]
I had the same issue on my sony vaio VGN CR590 after installing Ubuntu 20.04. I managed to fix (after a day's struggle) it by compiling and installing the r5u87x package from the[ source code]("https://bitbucket.org/ahixon/r5u87x/src/default/") itself.

The following steps worked for me.

1. It is beneficial to point to the "main server" in 'software and updates' tool in order to download any packages from. Install any pending updates.

2. Follow the below steps
[/FONT]```
[FONT=-apple-system]
sudo apt-get update -y
sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial 
hg clone [/FONT][http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)[FONT=-apple-system] 
cd r5u87x 
make 
sudo make install 
sudo r5u87x-loader --reload
[/FONT]
```[FONT=-apple-system]
[FONT=arial]Now you can open cam tools like cheese or guvcview and see the camera working. [/FONT][/FONT][FONT=arial];)[/FONT][COLOR=#172B4D][FONT=-apple-system]
[/FONT][/COLOR]

You saved me! :D It worked! Now I don't need to buy a new laptop, I can use this 2008 vaio for another couple of years!

Thanks!

---

### Post by monsterbash on 2020-08-23
> **bharan1 said:**
> [FONT=arial]
I had the same issue on my sony vaio VGN CR590 after installing Ubuntu 20.04. I managed to fix (after a day's struggle) it by compiling and installing the r5u87x package from the[ source code]("https://bitbucket.org/ahixon/r5u87x/src/default/") itself.

The following steps worked for me.

1. It is beneficial to point to the "main server" in 'software and updates' tool in order to download any packages from. Install any pending updates.

2. Follow the below steps
[/FONT]```
[FONT=-apple-system]
sudo apt-get update -y
sudo apt-get install libglib2.0-dev libusb-dev build-essential gcc automake mercurial 
hg clone [/FONT][http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)[FONT=-apple-system] 
cd r5u87x 
make 
sudo make install 
sudo r5u87x-loader --reload
[/FONT]
```[FONT=-apple-system]
[FONT=arial]Now you can open cam tools like cheese or guvcview and see the camera working. [/FONT][/FONT][FONT=arial];)[/FONT][COLOR=#172B4D][FONT=-apple-system]
[/FONT][/COLOR]

Unfortunately, bitbucket no longer supports mercurial, so the link to the project ([http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)) is not accessible anymore....
Do you know if there is another place to get those files from ?? Or, if you still have them, would you mind sharing ??

Thanks in advance !!!

---

### Post by karmacoma on 2020-09-08
> **monsterbash said:**
> Unfortunately, bitbucket no longer supports mercurial, so the link to the project ([http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)) is not accessible anymore....
Do you know if there is another place to get those files from ?? Or, if you still have them, would you mind sharing ??

Thanks in advance !!!

I'm exactly in the same situation as monsterbash, and like him I would like to know if there is any other place to download them or if you wouldn't mind sharing....

Thanks a lot!!!!

---

### Post by simonwilliams on 2020-12-04
> **karmacoma said:**
> I'm exactly in the same situation as monsterbash, and like him I would like to know if there is any other place to download them or if you wouldn't mind sharing....

Thanks a lot!!!!

@monsterbash, @karmacoma Did either of you get anywhere on this one ? I'm trying to re purpose an old Vaio SZ61 for my child for Home Schooling !

---

### Post by &amp;KyT$0P# on 2020-12-05
Is [this]("https://github.com/tmn505/r5u87x") it?

---

