---
title: "Panasonic KX-MB2000 printer"
date: 2013-03-30
forum: Hardware
---

### Post by wuz2blu on 2013-03-30
I am an ABSOLUTE linux beginner; i started trying to use it the day before yesterday! 

I am trying to figure out how to install my printer but i cannot figure out the instructions from the manufacturer (i can post the text of those if anyone wants to read them), and although i downloaded the driver package from the Panasonic website, i have no idea what to do with anything in it!

ANY help would be greatly appreciated. Thank you in advance.

---

### Post by DuckHook on 2013-03-31
Will try to help, but my lack of familiarity with your printer may be a hindrance.

1. Firstly, how is the printer connected to your box? Is is directly connected by USB or is it networked? If networked, is it wired or wireless?

2. Was it these instructions you downloaded? They are located at:

[http://cs.psn-web.net/support/fax/common/file/Linux_PrnDriver/Driver_Install_files/Ubuntu_ENG_003.pdf](http://cs.psn-web.net/support/fax/common/file/Linux_PrnDriver/Driver_Install_files/Ubuntu_ENG_003.pdf)

I have skimmed through them and they look pretty straightforward (but then, I'm an old Linux hound), so perhaps if you tell us exactly where you find them difficult we can better help to clarify.

3. The drivers are tar.gz which means that they are a compressed archive. This is similar to a Windows ZIP file and is uncompressed in a similar way. Just create a directory on your desktop and move the downloaded driver file into the directory. Then, following the instructions in the PDF, right click on archive and choose "extract". The remaining instructions seem straightforward to me. Just follow them step by step. If anything doesn't work for you, feel free to post back to this thread and someone will likely be able to help.

---

### Post by wuz2blu on 2013-03-31
> **DuckHook said:**
> Will try to help, but my lack of familiarity with your printer may be a hindrance.

1. Firstly, how is the printer connected to your box? Is is directly connected by USB or is it networked? If networked, is it wired or wireless
[COLOR=#008000]
Sorry i wasn't more clear in the details. My excuse is that i was tired and frustrated. (I am learning--or trying to--immersively; i deliberately did not "fix" my broken Windows box when i brought this Linux computer home so i'm forced to use and learn this "new" operating system. I'm too lazy to do it any other way. 
[/COLOR][COLOR=#008000]But none of that answers your question. I have it connected directly via USB.[/COLOR]

2. Was it these instructions you downloaded? They are located at:

[http://cs.psn-web.net/support/fax/common/file/Linux_PrnDriver/Driver_Install_files/Ubuntu_ENG_003.pdf](http://cs.psn-web.net/support/fax/common/file/Linux_PrnDriver/Driver_Install_files/Ubuntu_ENG_003.pdf)


I have skimmed through them and they look pretty straightforward (but then, I'm an old Linux hound), so perhaps if you tell us exactly where you find them difficult we can better help to clarify.

[COLOR=#008000]Yes, these are the same directions. They may be straightforward, but they seem to me to be in a foreign language. [/COLOR]:confused:  [COLOR=#008000]I[/COLOR][COLOR=#008000]  can decompress the file (i think that's the way that would be said...?) but once i get in there, i am completely lost. (I am spoiled with .exe files that you just double-click and they automatically (in hindsight, magically) install themselves.)

[/COLOR][COLOR=#008000]What i mean by "completely lost" is, i can get as far as opening the Terminal application, but do am i then supposed to type [/COLOR][COLOR=#b22222]“Dash home” -> ”Application” -> “Installed” -> “Terminal” in the menu [/COLOR][COLOR=#008000]? If so, with quotes, or sans? **Or** am i supposed to type [/COLOR][COLOR=#b22222]Dash home[/COLOR] [COLOR=#008000]and then hit Enter before typing[/COLOR] [COLOR=#b22222]Application[/COLOR][COLOR=#b22222][/COLOR][COLOR=#b22222][/COLOR][COLOR=#008000], etc.? See what i mean about my being a complete and utter Linux neophyte?[/COLOR]

3. The drivers are tar.gz which means that they are a compressed archive. This is similar to a Windows ZIP file and is uncompressed in a similar way. Just create a directory on your desktop and move the downloaded driver file into the directory. Then, following the instructions in the PDF, right click on archive and choose "extract". The remaining instructions seem straightforward to me. Just follow them step by step. If anything doesn't work for you, feel free to post back to this thread and someone will likely be able to help.

[COLOR=#006400]Thank you for being willing to help me. I look forward to being able to pay it forward someday![/COLOR]

---

### Post by DuckHook on 2013-04-01
> ...they seem to me to be in a foreign language.

I see. From this, I assume that you have never used the command line before. Okay, if you take it a small step at a time, you should be able to get to where you want to go.

> (I am spoiled with .exe files that you just double-click and they automatically (in hindsight, magically) install themselves.)

They just as magically install viruses and Trojans, but we will leave that for another day.

> ...am i then supposed to type “Dash home” -> ”Application” -> “Installed” -> “Terminal” in the menu ?

This sequence is a convention in all help forums and instruction manuals (including Windows) that stands in for clicking on the stated components and drilling down to each submenu. In the above case, it is just instructions for opening your terminal. You first activate your Dash, Click on Applications, then click on installed, etc.

> I look forward to being able to pay it forward someday!

This is a classy and generous sentiment that does you great credit. I hope the same for you!

Now to the matter at hand:

1. I assume that you have extracted the file to a directory on your desktop. If not, then the following instructions must be modified to get to the directory you extracted the file to. If the directory is on your desktop, then you should see *mccgdi-2.0.3-i686*

2. Open up a terminal. Type:```
cd ~/Desktop/mccgdi-2.0.3-i686
```Remember, in Linux, case matters. This command navigates you to the directory of the driver that you just extracted. The symbol ~ is just an alias for /home/your_user_name to save you the trouble of typing the longer path name. You can also see what the path to your driver is from the GUI file manager, Thunar. It might be a good idea to use Thunar to double check that the above path is correct.

3. To make sure that the driver has been properly extracted, do:```
ls
```This command lists all of the files in the current directory. Among the files, you should see:```
install-driver
```If you do not see this file, then you are not in the right directory, or you did not properly extract the file.

4. If 3 above is okay, then type:```
sudo ./install-driver
```The system will ask you for your login password. Type this in. The system will not respond to your typing in any way. This is a security precaution and is standard behaviour, but the system is accepting your password all the same. Once the password has been entered, you should see a whole bunch of operations flowing through your terminal window. Do not close your terminal until all of the operations have completed and you are back to the $ sign.

5. You should now have installed your driver. Hopefully, you can now follow the rest of the instructions in the manual under <Setting up the printer driver> because they have GUI examples to guide you.

Apologies for the delayed response. I've been entertaining family for Easter.

---

### Post by wuz2blu on 2013-04-01
These are wonderful instructions, thank you so very much! I was so tired and frustrated i haven't even turned my computer on since shortly after sending my last post! If anyone needs to apologize for a delayed response, it is myself and not you! Thank you for your many kindnesses, though, including that apology.

I want to tell you that i followed your instructions already and i have a result for you, but i am too tired right now to do more than try to read them. (They seem wonderfully clear and no "foreign language" is evident. ;) )  The truth is, i am not only tired but trying to get used to a new antidepressant that makes my mind really foggy. When i have a clear moment, assumedly later today, i will jump on this and immediately post here to let you know the result. I am very eager to do this, but i feel it's more effort (because of the fogginess, nothing against you or even Linux and its learning curve) than i am willing to expend right now. 

Again, thank you for your continuing help in this, not to mention your extreme patience with me!

P.S. I laughed out loud (on more than one occasion/reading) at the second part of your signature! Very well said indeed!

P.P.S. I feel my tag (under my username) should read "First Sip of Ubuntu"!

---

### Post by wuz2blu on 2013-04-01
DuckHook, you are a rockstar!  :KS Thank you so much! It printed beautifully, and not only that, the first thing i printed was an instruction sheet on how to install drivers for the built-in scanner! (Don't worry, with what you've taught me, i believe i can get through that on my own!)

I hope you don't mind all the exclamations, but i am so excited i can hardly type straight!

I hope your Easter went well and was thoroughly enjoyed by all. I'll let you get back to whatever it is you do when you're not helping helpless-feeling newbies such as myself.

Cheers!

-wuz

---

### Post by DuckHook on 2013-04-01
Given your enthusiasm, I predict that you will have a lot of fun learning and ultimately mastering Xubuntu. You have such a positive attitude towards it that you might find the following resources interesting:

For general introductions to Ubuntu and Linux:

[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://owlcroft.com/ubuntu/](http://owlcroft.com/ubuntu/)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

For a great write-up about how Linux differs from Windows:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

If you need more help getting the scanner to work, be sure to post on this forum. One of the best things about Ubuntu and Linux in general is the friendliness of the community. Always willing to help.

Enjoy, and Happy Xubuntuing.

---

### Post by wuz2blu on 2013-04-02
DuckHook;

I don't mean to drag this communication out; i'm sure you have other things to do, other folks to help, but i wanted to say thank you for the links. I really am excited to try them, especially the article about specific differences between "our"--can i say that yet?--O.S. and Windows! :P 

Thank you again for all your help. You are a wonderful recommendation (i can't think of the word i wanted to use) to this community (Linux users in general). Thank you for your patience, kindness, and knowledge shared.

Hopefully i will see you again. My dream is, one day i'll be able to "help" you by saying something encouraging like, "I see what you did there in helping that person with a really difficult issue. I would have done it the same way." [-o<


~wuz

---

### Post by DuckHook on 2013-04-03
> **wuz2blu said:**
> ...specific differences between "our"--can i say that yet?--O.S. and Windows!

Of course you can say that. Linux does not belong to anyone, and yet it belongs to everyone--even to those who don't use it. Like science or mathematics, or like language itself, it's founding and guiding principle is that it is a product and a legacy of humankind. Feel free (in the "speech" sense of the word) to self-identify with it.

> My dream is, one day i'll be able to "help" you by saying something encouraging...

You already have. This has been at least as rewarding for me as it has been for you. Being able to help is its own reward.

Good luck and Happy Xubuntuing!

---

### Post by bruce15 on 2014-03-29
Same printer.  Ubuntu LTS.

My Unix/Linux is very rusty but I'm comfortable at at a text terminal screen.

I can probably follow the directions referenced in the second post, but it's gone (404).
-----------
Edit:
Nevermind.  It's at [http://cs.psn-web.net/support/fax/common/file/Linux_PrnDriver/Driver_Install_files/Ubuntu_ENG_006.pdf](http://cs.psn-web.net/support/fax/common/file/Linux_PrnDriver/Driver_Install_files/Ubuntu_ENG_006.pdf)

---

