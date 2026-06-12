---
title: "Just what is this error?"
date: 2008-09-12
forum: General Help
---

### Post by icyest on 2008-09-12
I just installed a clean 100% ubuntu on my laptop. Seconds after I boot up on ubuntu for the first time, i get these 2 updates, as indicated by that red arrow on the top right.
[IMG]http://img135.imageshack.us/my.php?image=screenshot1zr2.png[/IMG]





[[IMG]http://img135.imageshack.us/img135/7356/screenshot1zr2.th.png[/IMG]](http://img135.imageshack.us/my.php?image=screenshot1zr2.png)




[IMG]http://img135.imageshack.us/my.php?image=screenshot1zr2.png[/IMG]

Clicking on install updates gives me these weird errors. Was there something wrong that I did in the creation of the Install disk? Should I have chose a lower disk write speed than maximum 24x? Why isn't disk write speed not discussed anywhere? Not even the official Ubuntu Guides say anything about disk write speeds when making your cd.


Re-Edit: Okay, this is ridiculous. The Ubuntu Forum's imaging systems are malfunction, just like my laptop. WHAT THE HELL IS GOING ON? 


6th Re-edit. This is the 6th time I've had to edit this thread. I don't understand why the insert image button is working. Someone needs to fix that too.

---

### Post by schizostatic on 2008-09-12
Would help if you stated the error you get.

---

### Post by Casper Hansen on 2008-09-12
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Idefix82 on 2008-09-12
> **icyest said:**
> 
Clicking on install updates gives me these weird errors.

How can anybody help you if you are not saying what "these weird errors" were.
There is nothing wrong with your disk since you installed Ubuntu successfully. The updates are downloaded from the internet, not from your disk. My best guess is that you don't have an internet connection, but I wouldn't have to guess if you had provided some specific info.

---

### Post by schizostatic on 2008-09-12
Cannont resolve host means either you are not connected to the internet or for some reason you can not dns the update host. Make sure your network card is either working with ubuntu or turned on.

---

### Post by icyest on 2008-09-12
I just re-edited the post schi.

---

### Post by iaculallad on 2008-09-12
Try to input the following command below in your terminal and post any error it will display:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by icyest on 2008-09-12
Here is a cleaner picture:

[[IMG]http://img261.imageshack.us/img261/1047/screenshotmn5.th.png[/IMG]](http://img261.imageshack.us/my.php?image=screenshotmn5.png)

---

### Post by Idefix82 on 2008-09-12
Why are you being so aggressive? You are getting an operating system for free and five people who don't know you and who have jobs and other things to do jump at your call to help you get started with it and you are cursing and foaming.
If you open the terminal (under Applications->Accesoires->Terminal) and type in
```
ifconfig -a
```
and give us the output then we will be able to tell you whether you are connected to the internet and if not then what you can do.

---

### Post by icyest on 2008-09-12
> **Idefix82 said:**
> Why are you being so aggressive? You are getting an operating system for free and five people who don't know you and who have jobs and other things to do jump at your call to help you get started with it and you are cursing and foaming.
If you open the terminal (under Applications->Accesoires->Terminal) and type in
```
ifconfig -a
```
and give us the output then we will be able to tell you whether you are connected to the internet and if not then what you can do.

cursing and foaming would be incorrect. The forum is not working for some reason, and I've tried repeatedly to get the imaging working. It's frustrating.

---

### Post by WRDN on 2008-09-12
It's not a problem with the installation itself, only that it cannot connect to the server. This happens often with the Medibuntu repositories.
You could try to solve it by selecting a different server to download the files from. To do this, click System > Administration > Software Sources. Now, select a different server from the "Download from: " combo box on the "Ubuntu Software" tab. You may want to select "Other" and then "Select Best Server".

---

### Post by Casper Hansen on 2008-09-12
> **icyest said:**
> Here is a cleaner picture:

[[IMG]http://img261.imageshack.us/img261/1047/screenshotmn5.th.png[/IMG]](http://img261.imageshack.us/my.php?image=screenshotmn5.png)

You're not connected to the Internet that could be the problem. And did you read my link?

---

