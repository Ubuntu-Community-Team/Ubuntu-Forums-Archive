---
title: "CPAN broken"
date: 2008-07-25
forum: General Help
---

### Post by sunnyl on 2008-07-25
Hi all,

I've been installing some modules for perl. At one stage I believe I did a an upgrade of CPAN from a non-root account, so there was just a heap of permission errors.

Now, I can still run cpan and get into the shell with the root account, but none of the other accounts can. Here is the error I'm getting:

```
sunny@files:~/Packages$ perl -MCPAN -e shell
Can't locate CPAN/HandleConfig.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/share/perl/5.8.8/CPAN.pm line 7.
BEGIN failed--compilation aborted at /usr/local/share/perl/5.8.8/CPAN.pm line 7.
Compilation failed in require.
BEGIN failed--compilation aborted.
sunny@files:~/Packages$
```

Is there a way to reinstall CPAN? (I've reinstalled Bundle::CPAN in the root account, but the error still happens on other accounts)

---

