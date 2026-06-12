---
title: "Transfering files via ethernet"
date: 2006-04-18
forum: Hardware &amp; Laptops
---

### Post by ubuntukid on 2006-04-18
Is it at all possible to transfer files between two computers by connecting them together with an ethernet cable? I want to transfer files between my laptop and my desktop computer. My laptop only has a diskett drive, no cd burner and I have large files I want to transfer so I thought I might be able to use the ethernet cable for it. Both the computers are running Ubuntu 5.10.

---

### Post by nife on 2006-04-18
[QUOTE=ubuntukid]Is it at all possible to transfer files between two computers by connecting them together with an ethernet cable? I want to transfer files between my laptop and my desktop computer. My laptop only has a diskett drive, no cd burner and I have large files I want to transfer so I thought I might be able to use the ethernet cable for it. Both the computers are running Ubuntu 5.10.[/QUOTE]


sure get ssh running and then the command scp will transfer between the two computers.

scp from to

kinda like 

scp some_file_to_copy myuser@192.168.0.2:~

that will copy some_file_to_copy from whatever machine you run that command on to the user myuser's home directory on the machine with ip 192.168.0.2

---

### Post by ubuntukid on 2006-04-18
I get a connection refused dialog box when I do this. How do I axcept the connection?

---

### Post by fmo on 2006-04-18
You need to install openssh-server

sudo apt-get install openssh-server

Once installed you should be able to connect from the other machine.

---

### Post by ubuntukid on 2006-04-18
Well it's transfering now but I have a question. The transfer is going very slow. Is it using my wireless internet connection or are ethernet cables just slow. And if it is using my wireless internett connection, how can I tell it to use the ethernet cable instead?

---

### Post by fmo on 2006-04-18
Ssh encrypt the data, so if your machine is a bit old, it might struggle.

With a Pentium4 1.7Ghz I usually get a 7MB/s speed between my 2 computers over a 100Mb switch.

You can try to type this on your openssh-server machine:
netstat |grep -i ssh

it should give you the IP address of the machine that is connected.

---

### Post by ubuntukid on 2006-04-18
[QUOTE=fmo]Ssh encrypt the data, so if your machine is a bit old, it might struggle.

With a Pentium4 1.7Ghz I usually get a 7MB/s speed between my 2 computers over a 100Mb switch.

You can try to type this on your openssh-server machine:
netstat |grep -i ssh

it should give you the IP address of the machine that is connected.[/QUOTE]

It took 30 sec to transfer one mb of data. This is no good. Is it because of an old computer?

---

### Post by ubuntukid on 2006-04-18
Hmm. Seems that it's using WiFi instead of my ethernet cable. How do I force it to use the ethernet cable instead?

---

