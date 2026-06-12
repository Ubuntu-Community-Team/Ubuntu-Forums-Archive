---
title: "Cron + sendEmail"
date: 2008-11-01
forum: General Help
---

### Post by the real omni on 2008-11-01
I've set up a cron job to send out an automated e-mail notification each week at 4pm on Thursday.

The problem is that the e-mail doesn't seem to arrive in my inbox nearly fast enough (and I assume that means it's taking just as long for other people). The e-mail is sent out at 4pm and I usually don't receive it until around 5pm.

As a temporary workaround I've just set it to send the e-mail out at 3pm instead but can anyone tell me why there would be an hour delay between sending and receiving? 

I know it's not just a case of my mail server being slow, because if I manually send an e-mail with the exact same content to the exact same mailing list, it appears in my inbox within 5 minutes every time... So it's clearly a problem with sendEmail.

Here's my crontab:
```

0 16 * * 4 /pro/scripts/GotW/gotw-irc_alert.pl /pro/scripts/GotW/distro.lst

```

Here's the perl script:
```

#! /usr/bin/perl

my @distro = <>;

chomp ( $list = shift @distro );

foreach ( @distro ) {
	
	chomp;
	$list = $list . "," . $_;
	
}

$list =~ s/,,/,/g;
system "sendEmail -f \"<my email address>\" -t \"$list\" -u \"IRC Conference\" -m \"IRC Conference starts at 6pm Mountain Time  --  irc://freenode/<channel>  --  channel key: <key>  --  Connection instructions: <link to PDF file>\" -s <smtp server>";

```

---

