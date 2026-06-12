---
title: "Lottanzb + Hellanzb = trouble?"
date: 2008-09-26
forum: General Help
---

### Post by Pastortom on 2008-09-26
Hay Guis!

Im having some trouble with Lottanzb and Hellanzb..

I've been using it for quite some time now, and in the beginning I didnt know Lottanzb/Hellanzb was capable of unpacking rar files after parring them..

But I realised after making some room on my main harddrive, that it sometimes actually unpacked the rar files as well..

Neat-o!

But.. it doesnt always do this.. sometimes it just moves all the rar-files to the designated "download" folder without unpacking them..

and other times THIS happens:
[IMG]http://img301.imageshack.us/img301/7829/nothingnv9.jpg[/IMG]

I see a folder and no rar files in the designated output folder in the "download" folder.. but when I doubleclick it I see NOTHING in it.. 

What the hell?

[IMG]http://img521.imageshack.us/img521/2156/foldertn7.jpg[/IMG]

As you can see in the previous folder it looks perfectly fine.. like Lottanzb/Hellanzb has parred/fixed/unpacked etc..

[IMG]http://img228.imageshack.us/img228/863/settingsqf1.jpg[/IMG]

My conclusion is that either the files were corrupt (needing par) and Lottanzb didnt realize that and didnt download the necessary par files..

What do you guys think?

But why doesnt it unrar the rar files that it moves to the designated "download" folder? I can simply unrar them myself after download, without any troubles.. why is it so hard for Lottanzb/Hellanzb?

Shout if you need any "computer specs" or whatnot.. though I doubt its related to that :)

Btw, i know how usenet works, with parring, etc, but I need to know how to make Lottanzb/Hellanzb work properly..

---

### Post by Pastortom on 2008-09-26
Anyone?

Bump!

---

### Post by Pastortom on 2008-09-27
bump! :D

---

### Post by Pastortom on 2008-10-05
anyone?!

---

### Post by aVirulence on 2008-10-17
Hi Pastortom.

You might want to take a look at this bug report: 

[https://bugs.launchpad.net/lottanzb/+bug/246101](https://bugs.launchpad.net/lottanzb/+bug/246101)


Short summary:

0) Close LottaNZB
1) Type gedit ~/.lottanzb/hellanzb.conf
2) Change:
          Hellanzb.UNRAR_CMD = "/usr/bin/unrar-free"
   to
          Hellanzb.UNRAR_CMD = "/usr/bin/unrar"

3) Start LottaNZB


From now on, all downloads should be extracted if they're not damaged! If you keep on getting empty directories, please let me know (or fill a bug report on [http://www.launchpad.net/lottanzb](http://www.launchpad.net/lottanzb) ) 

Thanks :-)

---

