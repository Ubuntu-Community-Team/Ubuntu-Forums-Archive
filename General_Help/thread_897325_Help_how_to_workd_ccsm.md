---
title: "Help how to workd ccsm"
date: 2008-08-22
forum: General Help
---

### Post by kizman on 2008-08-22
Hi there. I just installed ubuntu 8.10. I cant get the cube to work. My friend told me to use Add/Remove programmes and then search ccsm. Then install the file...

But the problem is that the computer i installed Ubuntu on to does not have internet. I got 3 computers =Þ. So yea i cant download the file that I need to download therefore i can not use the cube. Meaning i cant do anything cool to show my friends! :( 

Please someone help me get the file that i need.

---

### Post by sameerds on 2008-08-22
> **kizman said:**
> Hi there. I just installed ubuntu 8.10. I cant get the cube to work. My friend told me to use Add/Remove programmes and then search ccsm. Then install the file...

But the problem is that the computer i installed Ubuntu on to does not have internet. I got 3 computers =Þ. So yea i cant download the file that I need to download therefore i can not use the cube. Meaning i cant do anything cool to show my friends! :( 

Please someone help me get the file that i need.

One way to get ccsm is to download it on another machine. The Synaptic package manager available under System->Administration will help you do that. Start the package manager, and then search for ccsm (or even other packages that you want). When you mark it for installation, the manager will also mark other required packages.

Once you have marked all the packages you want, click on the File menu, and select "Generate package download script". This will create a shell script, which you can copy to some other Ubuntu machine which has access to the internet. Create a temporary folder on that machine, and run this script.

Once it downloads all the pacakges, copy this folder back to your machine. Now again run Synaptic, and in the File menu, select "Add downloaded packages", and then follow the instructions.

If the machine with the internet is not running Ubuntu, you can still download the packages manually. The script is basically a text file with a series of commands in it, one for each package that needs to be downloaded. Open the script in a text editor, and then you can see the link for each package. You can use these links to download the packages manually on that non-Ubuntu machine.

---

### Post by kizman on 2008-08-22
umm the computer with internet is windows xp 98. Umm  i want the package which will alow me to do the cube thing in Ubuntu. But also another problem... Im new ... Umm where do i download the package for the cube thing or ccsm???
 Sameerds thanks for the help so far =Þ

---

### Post by overdrank on 2008-08-22
> **kizman said:**
> umm the computer with internet is windows xp 98. Umm  i want the package which will alow me to do the cube thing in Ubuntu. But also another problem... Im new ... Umm where do i download the package for the cube thing or ccsm???
 Sameerds thanks for the help so far =Þ

Hi and welcome, Are you sure you installed 8.10 Intrepid, because it is still testing? It is not recommended for a primary system. You can look here for the packages 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by sameerds on 2008-08-22
> **kizman said:**
> umm the computer with internet is windows xp 98. Umm  i want the package which will alow me to do the cube thing in Ubuntu. But also another problem... Im new ... Umm where do i download the package for the cube thing or ccsm???
 Sameerds thanks for the help so far =Þ

Actually I already answered all that. The "cube thing" will become available when you install the ccsm package. You don't need to search for the link to this package ... Synaptic, the package manager already knows where it is. What I have said basically boils down to this:

1) The software called Synaptic is your friend when you need to install anything. It is accessed from by clicking on System in your Ubuntu desktop, and then clicking on "Administration"
2) In Synaptic, search for ccsm, and select it for installation. At this point, don't ask Synaptic to install it. Instead, like I said above, ask it to create a file containing the locations where the package is available. That file is called a "Package download script", but you don't need to worry about what that means.
3) Copy this file to your Windows PC, and open it in notepad. It will contain a number of lines, and each line will have a link that start with "http://.." . Download the package at each of these links ... you will need all of them.
4) Put these downloaded package files in one folder, and copy this folder back to your Ubuntu machine.
5) Then start Synaptic again, and install these downloaded files using the instructions I mentioned in the previous mail.

---

### Post by kizman on 2008-08-22
Thanks i love you so much.... :):lolflag:

---

### Post by kizman on 2008-08-22
Can we add friends on this forum thing because i got sameeds who will help me and i want to add you :lolflag:

Because im new!:guitar::guitar:

thats right im new and you guys are old :lolflag::lolflag:

---

### Post by kizman on 2008-08-22
I would also like to say thanks to overdrank forgot about you:lolflag:

---

### Post by kizman on 2008-08-22
[FONT="Arial Black"][/FONT]
i got a problem... In the Synaptic mangement thing... I searched ccsm and i was unable to find anything.... any ideas where its gone??? umm yea my bad i got ubuntu 8.04 the heron hardy

sorry that was fault for saying 8.10:confused:

Im new just remember that:lolflag:

---

### Post by overdrank on 2008-08-22
> **kizman said:**
> [FONT="Arial Black"][/FONT]
i got a problem... In the Synaptic mangement thing... I searched ccsm and i was unable to find anything.... any ideas where its gone??? umm yea my bad i got ubuntu 8.04 the heron hardy

sorry that was fault for saying 8.10:confused:

Im new just remember that:lolflag:

Hi and if you installed without a internet connection you may need to add repos to your sources list.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by kizman on 2008-08-23
how we add repos to resource list?

---

### Post by kizman on 2008-08-23
what repos????

---

### Post by overdrank on 2008-08-23
> **kizman said:**
> what repos????

Did you look at the link I posted earlier?
Have you tried using add and remove to install CCSM?
Under application, add and remove,select all available applications from the drop down menu. Then reload and search for CCSM.

---

### Post by kizman on 2008-08-23
Yea i have searched ccsm in add/remove....
But i need to download the file.... But i dont have internet on the Ubuntu. The computer with internet is my Windows Xp...
So i can download ccsm without internet and what i want to know is how to download using my windows xp the packages for ccsm and then move it to ubuntu. Also i would like to know how to install this ubuntu file... 
I know you might be thinking im dumb:lolflag:

But im new so yea....

Please help

---

