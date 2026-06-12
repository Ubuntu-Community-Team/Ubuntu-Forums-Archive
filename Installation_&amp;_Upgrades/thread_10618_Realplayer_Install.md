---
title: "Realplayer Install"
date: 2005-01-09
forum: Installation &amp; Upgrades
---

### Post by Sapper2ID on 2005-01-09
I'm starting to figure out this Linux thing (my 1st one). I have realplayer.bin in /home/ron. Ubuntu has great howto's and forums but I'm stuck on a little thing.  "$ cd browse_to_your_download_folder". I can do the rest of the install but what EXACTLY does this mean or would look like? I tried "cd /home/ron/RealPlayer10GOLD.bin" in the terminal. I even tried it with the installation cd in. Please push me over the bump. Thanks, Sap.

---

### Post by kleeman on 2005-01-09
You need:

cd /home/ron

then

chmod u+x RealPlayer10GOLD.bin 

then

./RealPlayer10GOLD.bin

---

### Post by Sapper2ID on 2005-01-09
All went well. I used the chmod 700 real...... instructions in the unofficial howto. Now it wont launch, I get Cannot launch entry

Details: Failed to execute child process "realplay" (No such file or directory)

How to uninstall and try again? OR, What Happened?

OK, couldn't uninstall so tried it again. I used your recipe and it worked fine but I don't have a launcher to start it. I did atleast get to the setup for realplayer but I can't get it to play a cd yet.

---

### Post by kleeman on 2005-01-09
At the prompt type

realplay

If that doesn't work find out where it installed by typing

locate -u

and then

locate realplay

This should give you the path

---

### Post by LongTooth on 2005-01-09
Another command for looking up packages you've installed is 'whereis packagename'. You'll get several listings. Usually its the one that starts with '/usr/bin/packagename'  or 'usr/local/bin/packagename'.

---

### Post by Sapper2ID on 2005-01-10
I've got many files in usr and opt. I'd love to uninstall all and start over with Kleemans option, that seemed to be the more trouble free of the 2 ways. Why doesn't ubuntu have a way to trash a file? I've found all the files but don't seem to have a valid "send to trash" option. 

Anyway, Thanks for the handy little "where the hell did I put that" command, gonna need that.

---

### Post by JsPr on 2005-01-10
[http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)

---

### Post by Sapper2ID on 2005-01-11
How do I UNinstall all of this so I can start over? Synaptic only shows .8. At this time that's the only way I know to delete a file like this. Can I use gedit, select all, delete? If so, that's a lot of files!

---

### Post by Sapper2ID on 2005-01-11
No Joy on either of the 3 ways suggested here. I'm missing something here(not suprising). I don't get a launcher in multimedia and the ones I've created don't seem to do anything. I still can't believe I can't just delete files out of these directories. I'm going to reinstall again, may #22 is the magic number. I learn more everytime.

---

### Post by Sapper2ID on 2005-01-11
Reinstall did the trick, I followed the unofficial guide in order.

---

### Post by nepaliman on 2007-07-13
hello everyone ..
i installed realplayer accidently in my desktop.. by following command 
[U]
[
Open the terminal and navigate to the file "RealPlayer10GOLD.bin". Type

 $ cd Desktop

#

Verify that the file is executable. If it isn't, type

 $ chmod a+x RealPlayer10GOLD.bin

#

Run the installer by typing
[/I]
 $ sudo ./RealPlayer10GOLD.bin

and enter your password.
#

Follow the prompts provided to finish installation.[/U][/U]
[/U]





now i want to uninstall it .. so i can again install it in proper drive ,, and i tried to search in add and remove .. but i couldnot find .. some one give me some help !
thanks in advance

---

