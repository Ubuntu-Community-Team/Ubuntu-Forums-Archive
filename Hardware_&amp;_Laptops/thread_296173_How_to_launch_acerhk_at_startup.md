---
title: "How to launch acerhk at startup"
date: 2006-11-09
forum: Hardware &amp; Laptops
---

### Post by theophane on 2006-11-09
Hello boys.
I've installed Ubuntu Edgy eft on my Acer Aspire 3023 WLMi and managed to make everything work, and i'm extremelly glad.
The last thing I would like to do, is to make my wifi connection being on at start-up. 
I modified my /etc/modules/ file and put those two lines in it :

[I]acerhk
echo 1 > /proc/driver/acerhk/wirelessled[/I]

Now my problem is that at start-up, acerhk seems to be loaded, but my wifi led is not on, and i still have to type *echo 1 > /proc/driver/acerhk/wirelessled* in a terminal in order to make my wifi connection work.

So my question is simple : how can I fix this, and make everything work at start-up ?

Cheers from Lyon, France

---

### Post by Lunar_Lamp on 2006-11-09
Well, you can remove the "echo 1..." from /etc/modules and try putting it in a simple bash script:

```
#!/bin/bash
echo 1 > /proc/driver/acerhk/wirelessled
```

Save this file and then then make it executable.

```
chmod +x filename
```

Then you can set up gnome to run the script when it starts by going to system>poreferences>sessions and then choosing the 3rd tab (start-up) and adding the path to the script there.

Thinking about it, I think you may just be able to enter the command directly into that without having to make it an executable script, but I'm not sure.

---

### Post by theophane on 2006-11-09
Done !!

And it works perfectly :)

Thank you

---

