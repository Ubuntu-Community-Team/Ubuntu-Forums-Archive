---
title: "help with study"
date: 2008-08-28
forum: General Help
---

### Post by JermainWijnhard on 2008-08-28
Hi for an exercise i have to make a tarfile in the background, bring it back to the foreground and cancel it. Problem however is that when i do it still get it in the forground and when i try to cancel i dont get my prompt back because its buisy with the output. If i open another CLI and do 'jobs' it says there are no jobs running. However, the tar file is still growing in size.

This is the command i'm giving:

> tar -c ~/test.tar /usr &

From this point on i'm getting output on my screen but I'm not getting a prompt to use the FG command to bring it back to the foreground. CTRL-C and CTRL-\ arent helping me either.

If i do 'fg' in another CLI is says

> -bash: fg: current: no such job

help? :confused:

---

### Post by Taxman415a on 2008-08-28
Well since this is an exercise I won't tell you exactly the problem, but it should become clear if you try your tar command without doing it in the background. Then read man tar. :) That is assuming you didn't make a typo writing in your commands here from what you are running. Ok, looking back over what you wrote, maybe it won't become clear, but reading the manpage will help in this case. Read all the available command switches.

---

### Post by mssever on 2008-08-28
> **JermainWijnhard said:**
> If i do 'fg' in another CLI is says
Job control is specific to a particular shell instance. So if you've backgrounded a process, you can only access it from that shell. Opening a new shell won't work.

Also, since you've backgrounded tar, you do have your prompt. You might not be able to see it due to the output, but it's there. Just start typing. You can also try redirecting the output so it goes to a file instead of your screen:
```
tar cvf tarfile.tar stuff > logfile 2>&1 &
```Note that if logfile exists, it will be overwritten and its original contents lost.

---

