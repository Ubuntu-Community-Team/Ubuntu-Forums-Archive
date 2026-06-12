---
title: "Decompress corrupted file"
date: 2008-09-19
forum: General Help
---

### Post by jofre on 2008-09-19
Hi everyone,

I am not able to decompress a backup file!!!

I had tones of stuff to backup so I did
$ tar -cvpjf test1.tar.bz2 books/
  (it compress contents of books into a file called test1.tar.bz2
  
I then, splitted the files :
split -b 4024m file_to_split Backup.tar.bz2

generating two files:
   Backup.tar.bz2.aa
   Backup.tar.bz2.ab

I did burn them into two dvdS. Then, after formatting the hard drive and installing xubuntu 8.04.1, I copied both file back into my home folder, and used the cat command:

	# cat Backup.tar.bz2.a* > Backup.tar.bz2

So far, so good. Then, I did:

	tar -xvjf Backup.tar.bz2

It starts decompressing, but then there is a moment when it stops and tell me:

	Input file = (stdin), output file = (stdout)

	It is possible that the compressed file(s) have become corrupted.
	You can use the -tvv option to test integrity of such files.

	You can use the `bzip2recover' program to attempt to recover
	data from undamaged sections of corrupted files.

	tar: Unexpected EOF in archive
	tar: Unexpected EOF in archive
	tar: Error is not recoverable: exiting now

So I did used the bzip2recover, it creates a huge amount of files of type rec0000Backup.tar.bz2

And then, I did:
	bunzip2 r*.bz2

which stops at the corrupted block, in my case rec03547Backup.tar.bz2

I renamed the corrupted file and then try "tar" in the others:
  tar xf r*.bz2

but I get:
  tar: Unexpected EOF in archive
  tar: Error is not recoverable: exiting now

I have spend the whole day with google, but I have not found a solution and I am starting to desperate. It must be a way to recover the information on the non-corrupted files, isn't it?

Thanks in advance,
Jofre

---

### Post by jofre on 2008-09-22
HAPPY END! (or as good as it could get)

I finally found a brilliant webpage:
[http://www.bestsolution.at/support/console/repair_tar_archives.html.en](http://www.bestsolution.at/support/console/repair_tar_archives.html.en)

with the solution on it (it had exactly the same problem as me)

---

