---
title: "I need some help with my startup script."
date: 2008-08-16
forum: General Help
---

### Post by Tom--d on 2008-08-16
Hello, 
I'm having a problem with my startup script. It doesn't work. But its very simple..
here it is,
```
#!/bin/bash
sleep 15 &
avant-window-navigator &
conky &
pkill /home/tom/.start
```

The last command is to kill the script as its just wasting ram.(a whole 400kb of it :p)
But...

It doesn't wait 15 seconds before it launches AWN and Conky + the pkill. It just launches them before the 15 seconds start. (or does the 15 seconds start at all, who knows).

Can someone help me out on this. I'm new to this scripting.

Also, what is #!/bin/bash ?


Thanks,
Tom

---

### Post by ad_267 on 2008-08-16
You need to remove the &'s from the end of the lines. That starts the next line without waiting for the previous to finish.

For the #! thing read this: [http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix))

---

### Post by Tom--d on 2008-08-16
> **ad_267 said:**
> You need to remove the &'s from the end of the lines. That starts the next line without waiting for the previous to finish.

For the #! thing read this: [http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix))

Right, I removed all the &'s. 
I ran the script and only AWN ran after 15 seconds. No conky and no pkill the script.
Help please :)
EDIT: 


That did it
```

#!/bin/bash
sleep 15
avant-window-navigator &
conky &
pkill /home/tom/.start
```

---

### Post by ad_267 on 2008-08-16
Whoops yeah you just need to remove the & after the sleep. If you don't have the & after awn and conky then AWN keeps running and the script won't go to the next line. My bad :)

---

### Post by Tom--d on 2008-08-16
> **ad_267 said:**
> Whoops yeah you just need to remove the & after the sleep. If you don't have the & after awn and conky then AWN keeps running and the script won't go to the next line. My bad :)

Ah, no problem :)
So why can't I have the & after sleep?

---

### Post by ad_267 on 2008-08-16
What the & does is leaves the command running and goes on to the next command without waiting for the previous command to finish. So if you have it after sleep it will start a sleep process but will run the next command without waiting for the sleep to end, so it's as if it doesn't sleep at all.

---

