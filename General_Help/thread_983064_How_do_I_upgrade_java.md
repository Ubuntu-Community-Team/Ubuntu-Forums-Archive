---
title: "How do I upgrade java?"
date: 2008-11-15
forum: General Help
---

### Post by Nymn on 2008-11-15
Apparently, I don't have the latest version of java on my machine and I can't get it to update. This is what version it says I have:


 java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Client VM (build 1.6.0_0-b12, mixed mode, sharing)


Can anyone help me out?

---

### Post by Mardoct909 on 2008-11-15
```
sudo apt-get update
```

If that doesn't do it, it might be a fetch it and compile it yourself deal.

---

### Post by Nymn on 2008-11-15
Just tried it, didn't work. Grrr!
How do I do a fetch and comp?

---

### Post by Bablefish on 2008-11-15
That is the thing with Linux they don't upgrade Java too often

---

### Post by Mardoct909 on 2008-11-15
Try their website. Might offer a source package and instructions.

---

### Post by taurus on 2008-11-15
There is no compiling for java.  If you want the latest version and it is not in the repos, then you have to download it from Sun's.  Then, just unpack it and run it.  You may have to configure your system to use the latest version then.

---

### Post by Nymn on 2008-11-16
How do you do that, though? I downloaded the .bin file from their site, but it won't open.

---

### Post by binbash on 2008-11-16
> **Nymn said:**
> How do you do that, though? I downloaded the .bin file from their site, but it won't open.

chmod +x filename.bin
sudo ./filename.bin

---

### Post by SouthernPott on 2008-11-16
I am having the same trouble.  From the Sun website I downloaded jre-6u10-linux-i586.bin and it is on the desktop.  

Their instructions say to open a terminal and type in " su ".  Then enter the password.  Done.

Change directory with " cd /usr/local/ " or whatever you are going to use.

Then it says to change the permission of the downloaded file to be executable by typing in " chmod a+x jre-6u10-linux-i586.bin ". 

This is where it stops for me.  I get the message 

chmod: cannot access `jre-6u10-linux-i586.bin': No such file or directory



FROM THE SUN WEBSITE:

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-6u<version>-linux-i586.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l

Make sure the installation file has executable permission

   6. Start the installation process.Type:
      ./jre-6u<version>-linux-i586.bin

I have just installed 8.10 and haven't used Ubuntu since last year so my skills (minimal at best) are rusty.

---

### Post by binbash on 2008-11-16
chmod: cannot access `jre-6u10-linux-i586.bin': No such file or directory

dude give this command where the downloaded file is located.If it is located at your home folder : 

chmod +x /home/usernamehere/jre-6u10-linux-i586.bin

Also be sure your file name is same as this (dont copy paste)

EDIT : you will also need after install : 

sudo update-java-alternatives -l
check the name of sun java, then
sudo update-java-alternatives -s
write sun java's exact name

---

### Post by SouthernPott on 2008-11-16
malcolm@malcolm-desktop:~$ su
Password: 
root@malcolm-desktop:/home/malcolm# cd /usr/local/
root@malcolm-desktop:/usr/local# chmod a+x jre-6u10-linux-i586.bin
chmod: cannot access `jre-6u10-linux-i586.bin': No such file or directory
root@malcolm-desktop:/usr/local# 


I appreciate the help you have offered but I am going to need a little more to go on.  I am presuming the file is located on the desktop since that is where it is showing.  The filename is correctly written.  

With that information and what my terminal looks like (above), what is it that I am not getting right.  Step by step please.

---

### Post by binbash on 2008-11-16
why are you locating /usr/local/ ??????

did you move downloaded .bin to there?

Dude the only thing you will do : 

Download .bin

Navigate to the downloaded file: (if you download it to your home directory go there) 
sample : cd /home/yourusername/
then
chmod +x yourfilename.bin
sudo ./yourfilename.bin

THat is it.

---

### Post by karlr42 on 2008-11-16
You're right, the file is probably on your Desktop(/home/malcolm/Desktop).

Check it's there, if so, the command is:
```

chmod a+x /home/malcolm/Desktop/jre-6u10-linux-i586.bin
```

---

### Post by SouthernPott on 2008-11-16
Sorry I took so long.

I did not capitalize the D in Desktop the first time around.  Corrected and now the icon on the desktop changed.  I am assuming this means it is now executable.

Not sure that I am completely understanding but I did get it to work by entering:

"  ./Desktop/jre-6u10-linux-i586.bin  "

The Sun license came up and it installed.

---

### Post by binbash on 2008-11-16
sudo update-java-alternatives -l

Theout put will be like :

sudo update-java-alternatives -l
[sudo] password for duyq: 
java-6-sun 63 /usr/lib/jvm/java-6-sun

then give this command


sudo update-java-alternatives -s java-6-sun

---

### Post by SouthernPott on 2008-11-16
Okay, I finally got through and it is showing as the newest version.  Unfortunately, the website, Pogo.com, is still saying it is either not installed or is incompatible.  

The instructions I was attempting to follow were from a link on their website to the Sun website.

I do have Java enabled in Firefox so I guess I will have to email them and ask for some more help.

Thanks for the help.

---

