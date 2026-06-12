---
title: "Brace expansion with scp in tcsh/csh"
date: 2008-10-10
forum: General Help
---

### Post by anlag on 2008-10-10
I frequently need to selectively copy a large amount of numbered files from various directories/servers, for which it seems appropriate to use brace expansion. On bash I would do, for instance:

scp [email]user@host:/some/dir/file_03{40..60}.dat[/email] .

...which could scp file_0340.dat, file_0341.dat and so on until file_0360.dat.

The problem is the syntax seems to be different in tcsh/csh, and as some machines I use have this set as default I'd like to know what the command is there. I know how to do file by file on t/csh, with for instance:

scp [email]user@host:/some/dir/file_03{40,41,42}.dat[/email] .

...but that's very inconvenient if I have to manually type in dozens or even hundreds of numbers.

I'm wondering if I didn't manage to use a [40-60] type expansion with ls, but I know I haven't got any of them working with scp yet, besides the bash way.

Anyone help me out?

---

### Post by KeyserSoze93 on 2008-10-10
i don't rely on brace expansion, since it doesn't seem to work in some places, with some commands. I would run the following command line:

```
for i in $(seq 40 60); do scp user@host:/some/dir/file_03$i.dat .; done
```

---

### Post by anlag on 2008-10-10
> **KeyserSoze93 said:**
> i don't rely on brace expansion, since it doesn't seem to work in some places, with some commands. I would run the following command line:

```
for i in $(seq 40 60); do scp user@host:/some/dir/file_03$i.dat .; done
```


Thanks for the suggestion, however I only get an "illegal variable name" error trying that. Willing to try it again though.

Would still also be nice to hear if the brace expansion can work though, it is after all a slightly more straightforward syntax.

---

### Post by iponeverything on 2008-10-10
> **anlag said:**
> I frequently need to selectively copy a large amount of numbered files from various directories/servers, for which it seems appropriate to use brace expansion. On bash I would do, for instance:

scp [email]user@host:/some/dir/file_03{40..60}.dat[/email] .

...which could scp file_0340.dat, file_0341.dat and so on until file_0360.dat.

The problem is the syntax seems to be different in tcsh/csh, and as some machines I use have this set as default I'd like to know what the command is there. I know how to do file by file on t/csh, with for instance:

scp user@host:/some/dir/file_03{40,41,42}.dat .

...but that's very inconvenient if I have to manually type in dozens or even hundreds of numbers.

I'm wondering if I didn't manage to use a [40-60] type expansion with ls, but I know I haven't got any of them working with scp yet, besides the bash way.

Anyone help me out?


Having different command interpreters on the clients does make this slightly more complex..

humm.. This should work if you have clients setup with keyed authentication: 

```
mkdir -p test/files
cd test
touch file_03{40..60}.dat
ls | awk '{print "scp foo@bar.com:/some/dir/"$1 " /files"}'|sh
```

---

### Post by geirha on 2008-10-10
Consider the following. 
```
scp user@host:/some/dir/file{1..2} .
# Is expanded locally into:
scp user@host:/some/dir/file1 user@host:/some/dir/file2 .
# Then it's executed
# Using quotes, however:
scp user@host:/some/dir/"file{1..2}" .
# This escapes the {1..2} locally, and is expanded on the server instead

```

In other words, if the user's shell on the remote machine is bash, you can use that bash-specific syntax inside quotes.

Also, the [] acts differently. Try ```
scp user@host:/some/dir/"file[4-5][0-9]" .
```

To copy file40-file59

---

### Post by anlag on 2008-10-10
I think I was unclear in my initial post; both client and host systems in this particular case are using csh, although admittedly sometimes I log on from bash as well. This time though, bash was just an example to illustrate the functionality I wanted.

And for this, the quotation marks and [][] worked perfectly, bit like so:

scp [email]user@host:/some/dir/"file-003[0-4][0-9]-*.dat[/email]" .

Which is particularly useful as the '*' in this case represents the 125 parts each 'file-xxxx' is in thanks to a messy parallel computing formatting. Now it's just a small bother of avoiding the "argument list too long" error, but that's another thread. ;)

Thanks again.

---

