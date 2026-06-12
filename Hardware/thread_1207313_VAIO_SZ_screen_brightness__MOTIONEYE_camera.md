---
title: "VAIO SZ screen brightness / MOTIONEYE camera"
date: 2009-07-08
forum: Hardware
---

### Post by scrambledarthur on 2009-07-08
Hello all!

I'm rocking a sony VAIO sz160p, and although I've downloaded all the latest NVIDIA graphics card drivers, there's still a problem with the adjusting of the screen brightness. 

I'm hella new at Ubuntu, so if there's anyone out there who could hook me up with a step-by-step I'd really appreciate it.

Also, the computer won't recognize the motionEYE built-in webcam. Any fixes for that? Thanks a bunch ubuntu community!

---

### Post by marcio_mi on 2009-09-17
Hi there,
same problems for me. If somebody could help, it would be greatly appreciated and I would be able to definitively get rid of Windows on my machine. Now I just keep it for the webcam

cheers

---

### Post by marcio_mi on 2009-09-17
Well, I solved the problem for the webcam, I guess I never tried hard before... just one problem, that I'll say at the end.

Here are the steps:
1. go to the page [http://bitbucket.org/ahixon/r5u87x/](http://bitbucket.org/ahixon/r5u87x/)
2. by running the command ```
hg clone http://bitbucket.org/ahixon/r5u87x/
```
you create a directory called r5u87x
3. Read and replicate each step of the README file in the directory

This will do the trick. Only one thing (and this is the problem): it seems that the webcam is not recognized unless I run the software with root privileges. For instance, if I try to run skype not as root, it will not pick up the webcam. Anybody knows why?

well, anyway I am pretty happy already. :guitar:

I just would like reassurances that by running skype as root I don't run into maybe bigger problems with the system....

---

