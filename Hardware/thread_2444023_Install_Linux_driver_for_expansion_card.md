---
title: "Install Linux driver for expansion card"
date: 2020-05-23
forum: Hardware
---

### Post by levde on 2020-05-23
I recently installed an [ORICO 2 Port USB3.0 PCI-E Expansion Card ]("http://www.orico.cc/us/product/detail/3886.html"), [ORICO PME-4UI]("http://www.orico.cc/us/product/detail/3886.html"), ([http://www.orico.cc/us/product/detail/3886.html)](http://www.orico.cc/us/product/detail/3886.html)) which uses a PCI-E slot to provide USB 3.0. It is the only card that I could find that claims to support Linux systems, and provides a driver called pme_series_expansion_card_driver.rar ([http://www.orico.cc/us/prodl/559.html](http://www.orico.cc/us/prodl/559.html))

                                 

naturally, it has not shown up in my Ubuntu software repository. 

Linux is a very complicated environment, and I have not figured out how to implement this driver. Although a GUI solution would be ideal, I can navigate the command line, if I know the correct commands. Can someone please help me? 

In windows, you would go to device manager, select properties, and then select "update driver". In  linux, I cannot even be sure the system sees the driverless hardware. But that's true for all of the hardware that Linux supports. I have no idea of how to know what hardware Linux sees, or how to connect the driver with the hardware. 

The strategy I have used so far is to try to add the driver to a repository, or designate the source website as a repository. The better strategy would be to place the driver in a folder where the Software Manager would see it. Or import it to that folder. But I'll use the strategy you suggest, if I can understand it. 

 I am boggled by the command line commands and switches. I need to know each command and each switch. In order. I need words that are not literal, that are meant as variables,  that I need to replace with a file name or web address, to be clearly designated as such. Please. I have read so many instructions online which do not make this distinction. If I have no idea when I am supposed to substitute my information, I can't use the instruction. 

This issue is very like many others where it comes to getting a system to recognize Linux software not listed in the repository, such as Tor. I hope someone can help me and I will learn something about using the complex system that Linux is.

Thank you, Levde

---

### Post by deadflowr on 2020-05-23
Open a terminal and run
```
lspci
```
post back the output.

---

### Post by levde on 2020-05-28
I'm still trying to get back to you, thank you for writing and for patience. Yesterday when I tried to post, I got a message instructing me to upload my images somewhere and link to them. I was too tired to jump that hurdle. Today I am looking for those instructions by sending a reply message with images that I expect to have rejected.

---

### Post by QIII on 2020-05-28
@levde

To post the results of the command suggested:  copy the results, click the # button above the text input box, place your cursor between the code tags that appear and copy the text of the results.

Please don't use images to post the results of commands in the terminal.

If you need to use images for other reasons, you may simply upload the file using the paperclip icon above the text entry box.  That will add an expandable thumbnail image to your post.

---

### Post by CelticWarrior on 2020-05-28
It's not Linux that is complicated, nor this forum. Unfortunately it's you who are the complicated one.

Starting with this last interaction you were asked to post the results of 'lspci'. Such results are terminal output that should be selected then right-click > copy or CTRL+SHIFT+C (SHIFT here being the only difference with almost all other apps regarding edition tools - copy, cut, paste). Here select Go Advanced, press "#" and past inside (right-click > paste or CTRL+V) in order to preserve format and readability.

Regarding your actual question and confusion... Linux has support for all USB3.x devices since 2009. Yes, before Windows had it natively. If I'm not mistaken that happened with the release of some service pack for Windows 7.
There's NOTHING you need to do to have it working, it's "plug'n'play". The same for any supported Windows version. The drivers you linked are for very old and now unsupported version of Windows and MacOS.

---

### Post by coffeecat on 2020-05-28
> **levde said:**
>  Yesterday when I tried to post, I got a message instructing me to upload my images somewhere and link to them.

Are you sure? We discourage people from uploading images off-site and linking to them. If you wish to attach images to your post, simply use the advanced message editor, and use the paperclip icon to upload your images to the forum server. That way you get clickable thumbnails which are far more satisfactory than linked off-site images. Neither do we review images before they are posted so I have no idea where your expectation of rejection comes from. 

I notice that you have not yet provided the output of lspci that deadflowr asked for. If you were thinking of including an image of this, please don't. Simply copy and paste the terminal output into your post and include it between BBCode code tags. That makes it much easier to read, and allows people to quote from the output if need be.

Link in my sig for how to use code tags if you need it.

---

### Post by levde on 2020-05-28
I'm trying.

---

### Post by levde on 2020-05-28
So I am struggling a lot with understanding Linux, so for me to feel Linux is complicated is reasonable. I would appreciate a more sympathetic response. I am certainly not attacking anyone. If I seem complicated the answer is yes, I am observant of many details others don't see and have questions others don't ask. I regard this as one of my assets. 
I appreciate the instruction on how to use the forum. when I sent my dummy post with pasted images, I got the instructions to use Ubuntu pastebin. I am on pastebin now. I will investigate the other options now. 
And yes, I have been trying to answer the request for "lspci" for a couple of days now. I am on the learning curve. Thank you for patience.

---

### Post by CelticWarrior on 2020-05-28
The request for the 'lspci' result is to confirm your addon card is correctly recognized as it should be, that's all.
Again, no drivers or any user action required. So the question is: Are you having a problem with it? If so please describe the actual problem.

---

### Post by QIII on 2020-05-28
Let's let the OP post the results before loading anything more on.

---

### Post by levde on 2020-05-28
Very helpful to know that the drivers are built in to Linux. When I investigated elsewhere, I didn't stumble across this info, this is the first time I'm hearing it. I am sorry the people who sell the PCIE cards don't just say "supported in Linux". I would not have struggled to find drivers and look for ways to load them. But it looks like it's all working fine. I will link to my Pastebin file where "lsusb -t" shows that both cards are active in 2.0 and 3.0. Thanks to folks on this forum for giving me the clues I needed to discover the truth, it's all working fine. 

I hope this is how this works, here is a url for my paste in PasteBin: [https://paste.ubuntu.com/p/wc9c8HtrWD/](https://paste.ubuntu.com/p/wc9c8HtrWD/)

---

### Post by levde on 2020-05-28
Hi deadflowr, 
Thank you for this question. It helped me to find the information that ultimately showed that my two expansion cards are working. The other commands that I found helpful were: "lsusb -t" and "lsusb -v". After pulling the cards, reviewing system data, inserting a flash drive to show which device was supporting it, I was able to identify usb buses from these cards and show that they are working fine. The problem was my ignorance and I am grateful for the help that educated me. 
Levde

---

### Post by deadflowr on 2020-05-28
> **levde said:**
> Hi deadflowr, 
Thank you for this question. It helped me to find the information that ultimately showed that my two expansion cards are working. The other commands that I found helpful were: "lsusb -t" and "lsusb -v". After pulling the cards, reviewing system data, inserting a flash drive to show which device was supporting it, I was able to identify usb buses from these cards and show that they are working fine. The problem was my ignorance and I am grateful for the help that educated me. 
Levde

Well, me among others ready to help.
If you've found the issues at hand have been satisfied [please mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"),
so that others may benefit.

---

