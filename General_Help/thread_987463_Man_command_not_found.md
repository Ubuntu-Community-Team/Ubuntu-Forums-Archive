---
title: "Man command not found"
date: 2008-11-19
forum: General Help
---

### Post by last1 on 2008-11-19
I have man-db installed and everything else that comes by default in the latest Ubuntu, but I tried going to a man page and it says man: command not found. The binary's still there in /usr/bin though. When I run it, it says 
bash: /usr/bin/man: Stale NFS file handle
When I try re-installing man-db, I get this error
E: /var/cache/apt/archives/man-db_2.5.2-2_i386.deb: unable to stat `./usr/lib/man-db/globbing' (which I was about to install)

---

### Post by last1 on 2008-11-19
Great, now perl won't run either. I get this when installing things now. Similar problems running Crossover.
                                                                                          
debconf: Perl may be unconfigured (Can't locate File/Spec/Unix.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/File/Spec.pm line 21.
Compilation failed in require at /usr/lib/perl/5.10/IO/File.pm line 12.
BEGIN failed--compilation aborted at /usr/lib/perl/5.10/IO/File.pm line 12.
Compilation failed in require at /usr/share/perl/5.10/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting

---

