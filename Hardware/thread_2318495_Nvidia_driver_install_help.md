---
title: "Nvidia driver install help?"
date: 2016-03-26
forum: Hardware
---

### Post by lexotulan on 2016-03-26
So I'm absolutely new to ubuntu and i'm using version 14.04 and i can't seem to get the .run file for my nvidia drivers to work i start the run file it finishes saying it has an error in language or something like that and gives me 4 options to either change the language or word settings Edit anyway cancel and something else i dont remember. I really don't know my way around ubuntu so if anyone could help that'd be amazing and severely appreciated.

Edit: i forgot to post that my graphics card is a Geforce GTX 960 and the drivers i'm trying to install are the latest 361.28 drivers that are listed on the nvidia website

---

### Post by weatherman2 on 2016-03-26
It's probably going to help if you can copy-and-paste the output from the terminal window into your thread here.

I assume you know the difference between 32-bit and 64-bit drivers?  If you installed 32-bit Ubuntu you need the 32-bit drivers; if you installed 64-bit Ubuntu you need the 64-bit drivers.

---

### Post by lexotulan on 2016-03-26
Yeah i've got the 64 bit version and copy-pasting the output? you mean the error that i'm getting or the string or code from the .run file?

---

### Post by weatherman2 on 2016-03-26
I assume you started the run file by opening a terminal, cd'ing to the Downloads folder, and typing "./NVIDIA-Linux-x86_64-361.28.run" (or whatever yours is called).  You could also type "sh ./NVIDIA-Linux-x86_64-361.28.run" .  Adding the "sh " in front of the command would avoid a permissions problem if you are getting an error about that.

But - copy and paste everything that was output in the terminal after you typed the command.  If there was a lot, just copy-and paste the last 20 or 30 lines at the end of the output.

FYI, every vendor seems to choose a different method to install drivers.  Having a file called ".run" may be unique to Nvidia - just a way they chose to name it.

---

### Post by lexotulan on 2016-03-26
oh thats odd i didn't put any command in the terminal just opened the run file is there a specific command i need to use instead? cause i just double click the file and it opens in a program called gedit and starts loading everything

---

### Post by weatherman2 on 2016-03-26
If you read down in Gedit (a text editor), it says, "If you were trying to download this file through a web browser, and# instead are seeing this, please click your browser's back button."  You are reading comments in the script file in the Gedit text editor.  You need to execute them, not read them.  (Sorry, the way they setup driver install was not the most intuitive for new users.)

You can try this:

Open a terminal (Ctrl Alt t)

Then type:

```

cd Downloads
sh ./NVIDIA-Linux-x86_64-361.28.run

```

I assume the run file was downloaded into your Downloads directory...

---

### Post by lexotulan on 2016-03-26
that'd be correct thank you for the help somehow i managed to make the nvidia driver work by using synaptic to download the driver and manage so my computer is recognizing the graphics card now. I'm really sorry this probably seemed like a huge waste of time. thank you very much though =)

---

### Post by weatherman2 on 2016-03-26
Not a waste of time.  Not everyone even has Synpatics installed - I don't think it's standard anymore so I didn't think to mention it.  Some drivers can't/won't be installed through Synpatic, but it sure is easier!  Note that the one you downloaded (the run file) from Nvidia is probably much newer than the one in the Ubuntu repositories (that you got via Synpatic), but that older driver you installed may work just fine.  If it does, you can call it good!

If you install other drivers, you may have to do it through the terminal similar to how I have described it above.

---

### Post by lexotulan on 2016-03-26
Alrighty thanks again for the help. I only found synaptic when trying to figure out why steam wasn't downloading through the software manager properly and had to use synaptic to get it to work so i figure if it worked there it might work for my graphics drivers and it did. thank for your time <3

---

### Post by ajgreeny on 2016-03-26
Assuming your query is now solved please mark this thread SOLVED using the Thread Tools menu at the top of the thread.

---

### Post by ra7411 on 2016-03-26
You might also try going into Dash, type drivers, you'll get "Additional Drivers", clicking that will make it search for drivers being used and maybe some additional choices.

---

