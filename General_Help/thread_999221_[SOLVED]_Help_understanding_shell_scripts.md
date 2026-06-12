---
title: "[SOLVED] Help understanding shell scripts"
date: 2008-12-01
forum: General Help
---

### Post by steviefordi on 2008-12-01
Apologies if this is the wrong forum but I'm not sure where to post.

I've been trying to learn bash scripting using a very good tutorial at [http://linuxcommand.org](http://linuxcommand.org).

I've not had a real problem with anything but cannot understand for the life of me the following if statement:

```
if ls /etc/*release 1>/dev/null 2>&1; then
```

Ok, what I do understand is the output from ls is being re-directed to some sort of black hole because it's not required. I also understand from the authors notes that it is the exit status of the ls command that we're interested in (although where that's being evaluated I can't tell).

I don't know what the 1 after the ls statement means, nor the 2 after the /dev/null re-direct.Neither do I understand the &1 at the end (another re-direction I guess, but to where?).

If anyone who knows this stuff can help clarify it for me I'd be most grateful.

Cheers
Steve.

---

### Post by jgoguen on 2008-12-01
Let's take it one step at a time :)  I'm going to try to make it simpler than might be necessary, but if you don't understand anything please let me know and I'll clarify.

First, starting with the command itself, ignoring the if block:
```
ls /etc/*release 1>/dev/null 2>&1
```

This runs the *ls* command with parameters */etc/*release*.  The * will expand this out to include everything in /etc/ that ends in 'release'.  The **1>** part could be simplified to just **>** but that's OK, either way it sends output on the standard output stream (file descriptor 1) to /dev/null.  A black hole, perhaps more popular as the "bit bucket".  The next part, **2>&1** tells the shell to append the standard error stream (file descriptor 2) to standard output.  This means that all output, regular and error, will go to the same output stream.  Normally, standard output and standard error are both displayed to you in the shell, but you can separate them by redirection.  The **2>** part means "redirect standard error", the **&1** means "append to standard output".  More on that later if you want/need explanations.  It's not important to understand file descriptors at this point, just know that Linux uses numbers internally to refer to data streams.  There are always three pre-defined streams:

[list]
[*]0 - This is standard input for the program/script.  You rarely (never?) need to refer to this specifically.
[*]1 - This is the standard output stream.  Normal (non-error) output goes here.  Redirect it with **1>** or simply **>**.
[*]2 - This is the standard error stream.  Error output goes here.  Redirect it with **2>**.
[/list]


The exit code for this is evaluated within the *ls* program itself.  Depending on what happens, ls knows whether it should exit with code 0, 1, 2, etc.  All programs have an exit code, and at the shell you can check the exit code of the last program you ran with this command:
```
echo $?
```

Now, putting the if block back in place:
```
if ls /etc/*release 1>/dev/null 2>&1; then
```
This basically says "if this command exits with code 0 (success) then do what comes next".  Here's a quick sample if block:

```
if ls /etc/*release 1>/dev/null 2>&1; then
     echo "ls worked!"
else
     echo "ls failed!"
fi
```

For this, if *ls* returns 0 (which is should) the output would be "ls worked!".  If it failed, you would see "ls failed!".  You would never see both.

Hope that helps clear things up.  Feel free to ask if you need more explainations.

---

### Post by vambo on 2008-12-01
> **steviefordi said:**
> Apologies if this is the wrong forum but I'm not sure where to post.

I've been trying to learn bash scripting using a very good tutorial at [http://linuxcommand.org](http://linuxcommand.org).

I've not had a real problem with anything but cannot understand for the life of me the following if statement:

```
if ls /etc/*release 1>/dev/null 2>&1; then
```

Ok, what I do understand is the output from ls is being re-directed to some sort of black hole because it's not required. I also understand from the authors notes that it is the exit status of the ls command that we're interested in (although where that's being evaluated I can't tell).

I don't know what the 1 after the ls statement means, nor the 2 after the /dev/null re-direct.Neither do I understand the &1 at the end (another re-direction I guess, but to where?).

If anyone who knows this stuff can help clarify it for me I'd be most grateful.

Cheers
Steve.

It's something like:
if ls exit staus isn't 0 then redirect standard error (the "1") to /dev/null and also redirect stdout (the "2") to stderror and hence to dev null.

I reckon the same could be achieved by

```
ls /etc/*release &> /dev/null
```

If I've made any errors in this I apologise in advance.

Finally, I can recommend the "Advanced Bash Scripting Guide", which you can get here: [http://linux.softpedia.com/get/Education/Advanced-Bash-Scripting-Guide-93.shtml]("http://linux.softpedia.com/get/Education/Advanced-Bash-Scripting-Guide-93.shtml")

Don't let the title put you off. This doc covers everything in great detail. I find it invaluable.

---

### Post by jgoguen on 2008-12-01
> **vambo said:**
> It's something like:
if ls exit staus isn't 0 then redirect standard error (the "1") to /dev/null and also redirect stdout (the "2") to stderror and hence to dev null.
Not quite, 1 is standard output and 2 is standard error.  Also, the redirection is unconditional, doesn't matter what the exit status is.

> **vambo said:**
> I reckon the same could be achieved by

```
ls /etc/*release &> /dev/null
```
Yes, this would also do the same thing.

> **vambo said:**
> Finally, I can recommend the "Advanced Bash Scripting Guide", which you can get here: [http://linux.softpedia.com/get/Education/Advanced-Bash-Scripting-Guide-93.shtml](http://linux.softpedia.com/get/Education/Advanced-Bash-Scripting-Guide-93.shtml)

Don't let the title put you off. This doc covers everything in great detail. I find it invaluable.
Doesn't seem like that can be downloaded right now.  At least I couldn't.  I get that from here though: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

There's also a PDF version if you want it offline: [http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)  

I do agree though, assuming you were linking to the same thing, this is a great guide.

---

### Post by lswb on 2008-12-01
The ABS Guide is a great resource. There is even a version in the repositories but it is usually out of date. You can get the latest at the author's home page,

[http://personal.riverusers.com/~thegrendel/](http://personal.riverusers.com/~thegrendel/)

Scroll down about 2 or 3 screenfuls to find the link

---

### Post by vambo on 2008-12-01
I always get these things (stderr and stdout and exit staus) upside down - sorry. That's where the ABS Guide is so valuable :)

---

### Post by steviefordi on 2008-12-02
Thanks for your time and help everyone, especially jgoguen. I'll be checking out that guide you've all reccomended.

I think I get it now, so I'll summarize as I understand it and you can correct me if it appears I'm still misunderstanding.

```
if ls /etc/*release 1>/dev/null 2>&1; then
  do this stuff
else
  do this instead
fi
```
will evaluate to
```
if 0; then
  do this stuff
else
  do this instead
fi
```

With **0** representing the exit code of ls. Anything other than 0 will go into the else block.

The **1>/dev/null** simply means redirect the standard output of **ls** to the bit bucket. As jgoguen said, the same as **>/dev/null** (which I understand), just explicity naming the standard output stream by putting **1** before the redirect.

**2>&1** means that if **ls** produces an error, which it will send to standard error (2), this must be sent to standard output as well. In this case, the bit bucket.

I'd quite like someone to explain the shorter version
```
ls /etc/*release &> /dev/null
```
that vambo posted.

cheers
Steve.

---

### Post by jgoguen on 2008-12-02
Pretty darn close.  The only thing I noticed is that if ls prints to standard error, it gets redirected to standard output, going *only* there, not *also* there.

As for the shortened command, I only know for sure that it works :)  I believe though that it works because **&>** means "append all output streams to the file name after the >".

---

### Post by steviefordi on 2008-12-02
Cheers jgoguen you're a star.

I was still a little confused about the standard error going also/only to the standard output, but you've cleared that up.

I've also done some experimentation with the 1> and 2> and am now sure I've got it. As for using &>, it makes sense that this refers to both S.O. and S.E., therefore that's how I'll think of it.

Thanks again..
Steve.

---

