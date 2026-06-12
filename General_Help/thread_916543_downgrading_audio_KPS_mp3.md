---
title: "downgrading audio KPS mp3"
date: 2008-09-11
forum: General Help
---

### Post by Dayne89 on 2008-09-11
I riped a cd to 320kps mp's, but i want another 128kps copy for my mp3 player, but my cd player is broken. is there any way to do this using the files i have on my computer?

---

### Post by Pro-reason on 2008-09-11
> **Dayne89 said:**
> I riped a cd to 320kps mp's, but i want another 128kps copy for my mp3 player, but my cd player is broken. is there any way to do this using the files i have on my computer?

Yes, it is simple.

Let's say you have a file called “Music.mp3” on your desktop.  

Do the following in a terminal:

```

cd ~/Desktop
sudo apt-get install lame
**lame Music.mp3**

```

There are also GUI tools to do the same, if you want to do it the hard way.

---

### Post by Dayne89 on 2008-09-11
thank you, but is there a way to do this to a large group of files from comand line instead of one by one?

---

### Post by Pro-reason on 2008-09-11
> **Dayne89 said:**
> thank you, but is there a way to do this to a large group of files from comand line instead of one by one?

Yep.

With most commands, you can just use the asterisk to make the command apply to all the files.  For example, &#8220;touch *.mp3&#8221; will update the timestamp of all files in the current directory that end in &#8220;.mp3&#8221;.  The asterisk has the same effect as if you had typed all the filenames into the command.

Unfortunately, the &#8220;lame&#8221; command does not accept a long list of filenames.  Instead, it expects just one input filename, and anything after that is taken to be the output filename.

To get around this, we need to use a loop, which will run through a list of things and run the command each time.

Use the &#8220;cd&#8221; command to go to the directory containing your MP3s.

```

mkdir 128bps
**ls -1 *mp3 | while read FILE ; do  lame "$FILE" "128bps/$FILE" ; done**
ls -lh ; ls -lh 128bps

```

That will create a new directory called &#8220;128bps&#8221;, create a list of all the files in the current directory that end in &#8220;.mp3&#8221;, feed that list into a &#8220;while&#8221; loop, then read each entry from that list and give it to the &#8220;lame&#8221; command, which will put its output into a file of the same name, but located in the &#8220;128bps&#8221; directory.  You can then get a listing of both directories, and compare the filesizes.

---

