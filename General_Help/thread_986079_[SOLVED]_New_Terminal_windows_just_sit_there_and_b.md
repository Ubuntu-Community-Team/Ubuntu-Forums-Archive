---
title: "[SOLVED] New Terminal windows just sit there and blink!"
date: 2008-11-18
forum: General Help
---

### Post by catfive on 2008-11-18
Hello everyone,

I hope someone can help me get to the bottom of this.

The issue is pretty much summed up in the title--when I open a new terminal window or tab, all I get is a blinking cursor until I hit Enter/Return, which gives me a normal prompt.

It sounds like a minor problem, but the issue is that hitting Return drops whatever incoming command initiated the terminal.

I'm not sure when this started, exactly, but I figure it has something to do with my profile.

I changed some options that sounded related (Run command as a login shell was unchecked which I don't think is the default, but checking that didn't fix it), and checked .bashrc and .profile for broken aliases, but found none.

What else should I look for?

Thanks in advance for any assistance!

---

### Post by catfive on 2008-11-18
One more quick bit of information:

Everything is peachy under a different user account!

---

### Post by catfive on 2008-11-18
Solved!

Took a closer look at .bashrc after renaming it fixed the error.

Earlier, I just deleted all the appends I had created (aliases), but didn't look at the upper sections closely, as I did not see how they would have changed.

Only a few lines in, the line "command line weather" stuck out like a sore thumb. I just installed weather-util yesterday, and I'm pretty sure I didn't put that there. 

I just un-installed and re-installed that package to see if it had done it automatically, but it did not (this time).

So I don't know how it got there, but that was the issue!

So kids, remember, if your new terminal windows hang, scrutinize your ~/.bashrc and ~/.profile files!

---

