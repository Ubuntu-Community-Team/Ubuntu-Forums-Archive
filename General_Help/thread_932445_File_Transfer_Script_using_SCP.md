---
title: "File Transfer Script using SCP?"
date: 2008-09-28
forum: General Help
---

### Post by igfud on 2008-09-28
Hello,

I am writing a script for a remote Ubuntu machine.  When the script completes, I want it to automatically save the resultant text file to my computer.  I thought this might be accomplished via the secure copy (scp) command.  I can call the scp command remotely, but I don't know how to give it my machine's password such that it can copy the files to my computer automatically.

I tried writing a similar version to automatically upload a file to the remote machine from my computer just to see if I could get it to work.  I tried:
```

scp /local/file/path user@remote_server:/remote/filepath < access.txt
```
where access.txt contains my password to the server.  When I ran the script in the terminal, I am just prompted for my password to the remote machine.  Is there some method that scp can find my machine's password either in a textfile or in the script itself so that it can automatically upload a file to my computer?

Thanks,
igfud

---

### Post by spiderbatdad on 2008-09-28
man page:```
man scp
```offers -i option to specify the file where the key is stored.

---

