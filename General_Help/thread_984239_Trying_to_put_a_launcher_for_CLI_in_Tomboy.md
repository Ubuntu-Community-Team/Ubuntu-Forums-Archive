---
title: "Trying to put a launcher for CLI in Tomboy"
date: 2008-11-16
forum: General Help
---

### Post by boof1988 on 2008-11-16
I'm trying to put a link/launcher to open Terminal in a Tomboy Note.

The thing I'm missing (I think), is the path to the command to open Tomboy.

I have tried this path (typed into Tomboy Notes) and it doesn't work [Note: I tried this cause I found a file with this /path/name]:
```
/usr/bin/gnome-terminal
```

Opening ***Run Application*** by <alt> + <f2> and typing *gnome-terminal* will start a Terminal session, so I'd like to understand how to start a Terminal session (as user) from Tomboy Notes.

Thanks...

---

### Post by Th3Professor on 2008-11-16
It appears tomboy notes is capable of recognizing things like internal/external links, email addresses, and directories, though as far as any actions like inserting actual functioning commands within the post-its, I'm not sure if that is possible. I checked the man file, googled it, tested/experimented with alternatives and had no luck. If it's vital that you have functioning commands (i.e. from /usr/bin) then you might consider another post-it program that does support that. Though, if you or someone else does find out or know of a way to include functioning commands within tomboy notes, I'd like to know! :) That would be a neat feature to have, though it seems like it might already be possible (considering all of the other actions available within that application).

---

### Post by boof1988 on 2008-11-16
> **Th3Professor said:**
> It appears tomboy notes is capable of recognizing things like internal/external links, email addresses, and directories, though as far as any actions like inserting actual functioning commands within the post-its, I'm not sure if that is possible. I checked the man file, googled it, tested/experimented with alternatives and had no luck. If it's vital that you have functioning commands (i.e. from /usr/bin) then you might consider another post-it program that does support that. Though, if you or someone else does find out or know of a way to include functioning commands within tomboy notes, I'd like to know! :) That would be a neat feature to have, though it seems like it might already be possible (considering all of the other actions available within that application).

Thanks for the reply.

I have figured out how to put the path & filename, this allows me to... say... open a txt file in gedit by clicking on the link.  Or open a webpage.  Or open a directory in Nautilus.

So... If I can figure out how to make a script or something and then add some sort of "preferred application" for a specified file-extension then maybe it is possible.

I'll keep this unsolved for now.  Until I know how hard it'll be to implement.

---

### Post by adrianogil on 2012-07-27
boof1988, did you have succeeded on such task? I'm also interested in such feature.

---

