---
title: "Bash Scripting Question"
date: 2008-10-01
forum: General Help
---

### Post by jjaeger4 on 2008-10-01
I've been working on teaching myself how to write bash scripts lately. To basically assist me with my work or do whatever. Anyways though, my question has to do with the following code. Also, sorry if there is a bit of redundancy:

```

#!/bin/bash
cd $HOME/bin/
pico
cd $HOME/bin/
chmod u+x *

```

Basically what this does for me is allows me to type the file name of this bash script to create another bash script, wherever I am in my directories. Because sometimes I have random ideas and don't feel like navigating out of what I am doing and into what I want to do at the time. 

This will take me to my bin directory, start up pico, type away at my new script..., then it will make the file executable so I can run it as a script.

My question is:

Instead of using chmod u+x * can I grab the file name from pico using bash?

I don't know what I would name a script ahead of time. I want to replace * with the name of whatever I save the file as.

Thanks for any help!

- Jesse

---

### Post by ianhaycox on 2008-10-01
You could use,

```
chmod u+x `ls -tr | tail -1`
```

which will chmod the newest file in the directory. Obviously this fails if you write out more than one file in pico.

---

### Post by jjaeger4 on 2008-10-01
Thanks much! That's basically all I was looking for but I couldn't figure out how to word a Google search for it.

I'll give it a try when I get back around to the script. Thanks again.

---

