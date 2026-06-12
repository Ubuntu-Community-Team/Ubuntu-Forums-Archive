---
title: "Redirect output from running processes - how?"
date: 2008-10-22
forum: General Help
---

### Post by JohnFH on 2008-10-22
I've had a look around for the answer to this, but as it's quite a specific question, finding the answer is proving difficult.

I'm using dd to erase data on a hard drive and, running the command in the background, I know that sending the USR1 interrupt to the process will cause it to write to stderr.  Now I called the dd command without redirecting the stderr, so my question is this - is it possible to redirect the output (stdout) or stderr of a process that is already running?

I know all about 1> 2> redirection commands, but these are only useful when starting the process.  I want to be able to redirect the output of a long running process - is that possible?

Thanks.

---

### Post by JohnFH on 2008-10-22
No-one know the answer to this?

Thanks.

---

### Post by snova on 2008-10-22
I don't know of a way to do this. I don't think it's possible.

It has something to do with the way redirection works. I don't know the specifics, but I'm fairly certain it has to be done either prior to starting the program or from the program itself.

I Googled a bit (this thread is one of the results), but the closest thing I could find involved using a debugger to modify the file descriptors. You could always try writing a script to automate it, I guess. Two links I found with the same suggestion:

[http://etbe.coker.com.au/2008/02/27/redirecting-output-from-a-running-process/](http://etbe.coker.com.au/2008/02/27/redirecting-output-from-a-running-process/)

[http://abreau.org/howto/gdb/redirecting-stdout.txt](http://abreau.org/howto/gdb/redirecting-stdout.txt)

---

### Post by JohnFH on 2008-10-23
Thanks for that.  Yeah I had doubts about whether it was possible at all.  Those links are interesting though and I didn't come across them in my searches, so thanks.

---

