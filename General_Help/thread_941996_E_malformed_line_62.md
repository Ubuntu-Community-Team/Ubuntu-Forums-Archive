---
title: "E: malformed line 62"
date: 2008-10-08
forum: General Help
---

### Post by Saved0ne on 2008-10-08
i finally got ubuntu on my dekstop and its working fine... but..........

i have an error sign up at my top right corner... and its for the package manager... and whenever i type something in the terminal... like:

sudo apt-get install (insert)

it says:

"E: Malformed line 62 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read."

can anyone help?

thanks in advance.
-Chris Voeltz, Website owner
[www.TrueGameStudios.com](www.TrueGameStudios.com)

---

### Post by aysiu on 2008-10-08
Looks to me as if there's a malformed line 62 in your /etc/apt/sources.list file.

That means there is a text file called *sources.list*

That file lives in a directory called */apt* that, in turn, itself lives within another directory called */etc*

So all you have to do is open that file in a text editor, find the offending line, and delete it.

Let's go ahead and see what that line looks like, though. Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here: ```
cat /etc/apt/sources.list
```

---

### Post by bodhi.zazen on 2008-10-08
or, for ease of reading,

```
cat -n /etc/apt/sources.list | grep 62
```

---

