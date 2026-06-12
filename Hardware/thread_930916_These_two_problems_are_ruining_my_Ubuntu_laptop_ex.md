---
title: "These two problems are ruining my Ubuntu laptop experience."
date: 2008-09-26
forum: Hardware
---

### Post by jorgecarrillo150990 on 2008-09-26
Im not sure if this goes in this forum, but here it goes.

I have been having one of this problems for a while, and let me explain it to you. I run Hardy. You know how at 34 number of times you start Ubuntu, an automatic fsck is made.
I usually press Esc, because I am in a hurry, but one time when I left Ubuntu do the fsck an error happened and I was sent to the terminal.  The first pic included is regarding this problem.
[IMG]http://i73.photobucket.com/albums/i222/MexAlbum/100_1115.jpg[/IMG]

One curious thing that happened is that the first time it failed to do the fsck it had 95% progress, today it just had 5% and BAM! to the terminal.

I can live with this problem, because I usually skip the fsck process. But there is the new problem, and the one that I think is the worst, becuase I can't handle it.

I do the usual skipping of the fsck and go to the GDM. Log in and wait to my desktop to charge. Today I did the same thing until I thought I had been waiting for a long time and my desktop didn't appear. I did the Ctrl+Alt+Backspace to go back to the GDM and a blue screen appears saying that:

THE X SERVER COULDN'T BE STARTED DUE TO AN INTERNAL ERROR, THAT I SHOULD CONTACT THE ADMINISTRATOR AND WAIT FOR A DIAGNOSIS.
AT THE END IT SAYS THAT MEANWHILE THE SCREEN WILL BE DEACTIVATED AND THAT I SHOULD RESTART THE GDM WHEN THE PROBLEM IS SOLVED. 
[IMG]http://i73.photobucket.com/albums/i222/MexAlbum/100_1117.jpg[/IMG]

But the problem is that I don't know what went wrong, it doesn't give any details. So im counting on you to help me.

---

### Post by pelle.k on 2008-09-26
Well, this is how to use fsck;
```
Usage: fsck.ext3 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list

```

Try;
```
fsck.ext3 -pyf
```

You might also want to;
```
fsck.ext3 -cf
```
To check for bad sectors, when the problem is fixed.

---

### Post by jorgecarrillo150990 on 2008-09-26
Thank you, you are the first person in the 4 forums I posted this that gave me an answer.

Im going to try this right now.
Now, will it solve the X-server problem too?

---

### Post by pelle.k on 2008-09-26
Possibly. However, we will know more once the fsck is done.
Don't skip the fsck. It will continue nagging you until you let it finish, but once you do it, it'll be at least 30 mounts until the next time.

---

