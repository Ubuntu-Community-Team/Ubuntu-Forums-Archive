---
title: "Overclocking ATI with ROVCLOCK"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-10-10
Hi,,
trying to compile this prog ..
So far......
DL'ed file to desktop...rovclock-0.6b.tar.bz2
extracted to desktop...rovclock-0.6b

cd /home/roderick/Desktop/rovclock-0.6b
./configure ...problems start. 

roderick@ubuntu:~/Desktop$ cd /home/roderick/Desktop/rovclock-0.6b
roderick@ubuntu:~/Desktop/rovclock-0.6b$ ./configure
bash: ./configure: No such file or directory
roderick@ubuntu:~/Desktop/rovclock-0.6b$

I tried to "make" even though it didnt config.. and it made and executable file in the folder.. called "rovclock" 

Tried to "make install" but nothing happened..
cant open the prog at all (clicking or in terminal)
Readme is no help and ther is no install file..(iv read all the files ..nothing)

Here is the read me..
........................................................
Radeon overlocking utility version 0.6b

It tries to detect the reference clock (xtal) from the 
video BIOS, if this doesn't work you can specify it manually. 
Try 1432 or 2950 if the default value of 2700 does not show the 
correct frequency when using -i:

rovclock -x 1432 -i

Cards reported to work:

Radeon 7500
Radeon 9000
Radeon 9100
Radeon 9500 (Pro)
Radeon 9600
Mobility FireGL T2
Mobility Radeon 9600 M10
Radeon 9700 (Pro)

Use the memory timing options with care and login via ssh
to make changes. So you can revert them back if your screen
corrupts:

rovclock -t tRcdRD:7

Any comments, patches, bug reports to: [email]se.witt@gmx.net[/email]
...............................................................................................................
Anyone get this working...? Care to let me in on how to do it..
thanx

---

### Post by floyd27 on 2005-10-10
figured it out..
its just "make"
then ./rovclock-0.6b -i 
that will give you the syntax and your current clock speeds.

you can then 
sudo ./rovclock-0.6b -c (new mhz) -m (new mhz) for core and mem respectively..

I havent found any GUI and i dont thing there is one..
Dont know if the setting hold after a boot either..Havent tried yet..

---

### Post by Cobra78 on 2005-10-11
I now that's is not really a solution to your problem in linux, but i think the better way to overclock a video card is finding the maximal frequencies in wondows with dedicatet tool (ati tray tool or ati toll), and then editing the viedocard bios :)

---

### Post by floyd27 on 2005-10-11
I wouldnt edit the bios and change the speed permenently..
I like to be able to just set it to the higher speeds when i need it.. 
But that would work too. :)

---

