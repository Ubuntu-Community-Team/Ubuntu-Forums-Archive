---
title: "How to install"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by Abdel-Rahman on 2009-02-25
Hello.

How can i install .bin files?

---

### Post by stumbleUpon on 2009-02-25
> **Abdel-Rahman said:**
> Hello.

How can i install .bin files?

make the file executbale

```
chmod +x binFile
```

and then execute it (from the directory in which the file is present)

```
./binFile
```


However make sure you understand what the file is doing or that it is from a trustworthy source. See here

[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)

---

### Post by Abdel-Rahman on 2009-02-25
> **stumbleUpon said:**
> make the file executbale

```
chmod +x binFile
```



where do i type this?

---

### Post by stumbleUpon on 2009-02-25
> **Abdel-Rahman said:**
> where do i type this?

In a terminal. Applications > Accessories > Terminal. Go to the directory in which the .bin file is present. And then execute the above commands.

---

### Post by Abdel-Rahman on 2009-02-25
I do not have the Accessories option, where can i change this?

---

### Post by Abdel-Rahman on 2009-02-25
or rather, how can i acces this?

---

### Post by ugm6hr on 2009-02-25
What version of Ubuntu are you using?

Every version for over 2 years has an Applications -> Accessories menu.

---

### Post by Abdel-Rahman on 2009-02-25
i have 8.10 intrepix. i have a programs menu (danish) but there is no "assecories" there, only some others. But is there not any other way to acces other than that menu?

---

### Post by stumbleUpon on 2009-02-25
Which variant of ubuntu...? ubuntu / kubuntu / xubuntu

If gnome is installed, then

```
Alt + F2
```

and then typing

```
gnome-terminal
```

should give you a terminal

---

### Post by Abdel-Rahman on 2009-02-25
can somebody please help, i really need to install some things.

---

### Post by stumbleUpon on 2009-02-25
Have you not been able to get a terminal....?

---

### Post by Abdel-Rahman on 2009-02-25
yes, i have, but that code you gave in the begining does not work, it says "no such file or directory".

---

### Post by stumbleUpon on 2009-02-25
In the terminal, you have to navigate to the directory where the .bin file is located and then use the commands i mentioned earlier

---

### Post by ad_267 on 2009-02-25
You can also just right click on a file in the file browser and under it's properties there should be an option to make the file executable. Then you can double click on the file to run it. But depending on what kind of application it is you may need to run that .bin file from the terminal.

---

### Post by Abdel-Rahman on 2009-02-25
it is in this folder: "abdur-rahman" and then "Downloads", when i enter this it says: "command not found"

---

### Post by ambdeep on 2009-02-25
Just drag the .bin file to the terminal and press enter.......SIMPLE
It WORKS!!!!!!!!!!!!!!!!!!!

---

### Post by stumbleUpon on 2009-02-25
Yes....you have to go to that directory using the 'cd' command in the terminal.

See here for how to navigate to a direcoctory using the terminal

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by Abdel-Rahman on 2009-02-25
> **ambdeep said:**
> Just drag the .bin file to the terminal and press enter.......SIMPLE
It WORKS!!!!!!!!!!!!!!!!!!!

i dragged the file, but, it says that there is no program installed for this.

---

### Post by Abdel-Rahman on 2009-02-25
Is there not some easy way to do this? It is supposed to be better than windows, but at least windows is not so complicated! You just cklick on the file and that is it! What is all this?

---

### Post by Abdel-Rahman on 2009-02-25
amdeep, what do i need to install to be able to just drag the file?

---

### Post by Abdel-Rahman on 2009-02-25
does one have to be a complete nerd or worship ubuntu to be able to install a program? who has patience for this? it just gets more and more complicated.

When i type "cd" in the terminal it says that i dont have permission.

It just gets more and more comlicated, how is a simple person suppose to be able to figger this?

---

### Post by Abdel-Rahman on 2009-02-25
i can get it to go to the folder, but it does not want to run the file, it says that you do not have a program installed for this, where can i find this program, can somebody please tell me?

---

### Post by infinitejones on 2009-02-25
Dude. Chill out. Ubuntu is different from Windows, and one of the things you'll find using these forums is that you need to relax, be polite, explain your problem fully, and give people time to reply to you. Nobody here is paid, nobody is obliged to help you, and there are a lot of other posts where the people with problems are asking sensible questions and doing it properly.

Now, onto your problem. Tell us the exact name of the .bin file you've downloaded, and I'll tell you what to type in order to run it.

I might not be able to respond to you **immediately** so please bear with me...

---

### Post by Abdel-Rahman on 2009-02-25
> **infinitejones said:**
> Dude. Chill out. Ubuntu is different from Windows, and one of the things you'll find using these forums is that you need to relax, be polite, explain your problem fully, and give people time to reply to you. Nobody here is paid, nobody is obliged to help you, and there are a lot of other posts where the people with problems are asking sensible questions and doing it properly.

Now, onto your problem. Tell us the exact name of the .bin file you've downloaded, and I'll tell you what to type in order to run it.

I might not be able to respond to you **immediately** so please bear with me...

Thanks man, i know and it was not to be rude, i just got anoyed over my computer. it is java that i try to install the file is called: jre-6u12-linux-i586 (.bin).

---

### Post by infinitejones on 2009-02-25
OK. Here is what you need to do. I assume from your previous posts you've opened up a terminal and used the cd command to get into the directory where the .bin file is saved. You can check by typing 'ls' (that's LS, but in small letters) - if jre-6u12-linux-i586.bin appears, you're in the right place.

Anyway - first type this:
```

chmod +x jre-6u12-linux-i586.bin
```

This tells Ubuntu that you want to execute the file. (By the way, there's a big difference between Windows and Ubuntu/Linux - Windows assumes that any .exe file that you might have downloaded from somewhere can be executed. Ubuntu requires you to explicitly tell it that you want to executed it. I'll leave you to work out which one's safer!)

Anyway, if nothing happens (other than the command prompt appearing again), it's all worked, so type

```
./jre-6u12-linux-i586.bin
```

That actually installs what you've just downloaded.

However, this brings me to a different point - do you have a specific reason for installing this? It looks like you're installing a java runtime, and there's a different (Ubuntu specific) way of installing stuff like this, which is different from the Windows "download-a-file-and-install-it" routine that we've gone through here. The "Ubuntu specific" way is likely to be more appropriate and cause you fewer problems in future than doing it this way.

Are you familiar with something called Synaptic?

---

### Post by linux_tech on 2009-02-25
> **Abdel-Rahman said:**
> Thanks man, i know and it was not to be rude, i just got anoyed over my computer. it is java that i try to install the file is called: jre-6u12-linux-i586 (.bin).

you may also try
```
 
sudo apt-get install sun-java6-plugin

```

or if you want to use synaptic-

System>Administration>synaptic package manager 
search for sun-java6-jre then check box and mark for installation
then click apply

During the java install I think you will need to press your enter and tab 
keys a couple times to complete the install

---

### Post by Abdel-Rahman on 2009-02-25
> **linux_tech said:**
> you may also try
```
 
sudo apt-get install sun-java6-plugin

```

or if you want to use synaptic-

System>Administration>synaptic package manager 
search for sun-java6-jre then check box and mark for installation
then click apply

During the java install I think you will need to press your enter and tab 
keys a couple times to complete the install

Thank you, it worked.

thanks infinitejones too for you help

---

### Post by zeroemissions on 2009-02-25
sorry missed the third page :)

---

### Post by ad_267 on 2009-02-26
Looks like we made that a bit more difficult than it had to be. This is worth a read, it explains pretty much everything you need to know about installing software in Ubuntu: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

