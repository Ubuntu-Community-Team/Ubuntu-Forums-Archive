---
title: "Batch equivelant"
date: 2008-09-10
forum: General Help
---

### Post by bullfroghrr on 2008-09-10
Hi new to the forums and new to Ubuntu!  2 weeks ago I installed Hardyn Heron on my laptop, while it works very well for the most part, flash causes my sound to go away intermittently.  I have found that simply running 
sudo alsa force-reload 
will get it working again. How can I go about making a simple file that will execute this command?

---

### Post by russo.mic on 2008-09-10
You could easily make a script to run that.

Simply open up a new file, put the code in, then save.

execute this command to make it executable

sudo chmod +x 'filename'

then, ./'filename' to execute.  You could even make a launcher on  your desktop.

Russo

---

### Post by silverglade00 on 2008-09-10
From the title, I suspect you are used to writing DOS batch files. This is similar, but there are a few differences. 

```

#!/bin/bash
sudo alsa force-reload

```

Then save and use the chmod command that russo.mic gave. The thing about writing bash scripts versus DOS batch files is that you need the #!/bin/bash line first before your commands.

---

### Post by bullfroghrr on 2008-09-11
Thanks for your help that did the trick

---

