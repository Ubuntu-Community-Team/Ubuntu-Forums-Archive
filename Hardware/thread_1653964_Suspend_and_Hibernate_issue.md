---
title: "Suspend and Hibernate issue"
date: 2010-12-27
forum: Hardware
---

### Post by jl2035 on 2010-12-27
I'm using Ubuntu for 2 or 3 years now and I hate to write about this...and this is not the first time I do.

Suspend and hibernation does not work on most laptops that I had in my hands: HP 6715s, Dell Studio 1555, eMachines E525,... and this is just a few of them...but HP machines are the worst! 

Ubuntu has many problems(and so does any other operating system) but this is the biggest one. I can't live like this forever. Closing the lid of the laptop...I've seen this on a television 15 years ago...it can't be such a big deal! 

I checked many websites and forums, but whenever I ran into a solution or workaround it does not work for me(currently Dell Studio 1555). 

And I have to say... I love Linux, I love Ubuntu, but we really have to fix this...

---

### Post by Mr James on 2010-12-27
Google Xorg-edgers ppa and try that.

---

### Post by jl2035 on 2010-12-28
So what is this package...?

---

### Post by jl2035 on 2011-01-28
I finally found the solution(ubuntugeek.com) for this after years!! 

For those whit the same problem:

Open the Terminal and type:

```
sudo gedit /etc/pm/config.d/00sleep_module
```

Add a line at the end of file
```
‘SUSPEND_MODULES=”xhci”
```

That's it!

The guy who discovered this is a genius!

---

