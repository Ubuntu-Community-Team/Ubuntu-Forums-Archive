---
title: "apt bug?"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2009-09-23
Hi,

I'm trying to update from a repository that uses https rather than the more normal http.

It requires a username password, which I understand can be put into the url as ```
<https://username:password@domain/path>
```.

However, when the password contains an '@' symbol, it doesn't seem to work.

To me, this seems like an apt bug.

I expect it's splitting the string wrongly, like this :

Assuming...

```
/([^:]*)://([^/]*)/(.*)/;
$protocol = $1;
$usernamePasswordDomain = $2;
$path = $3;
```

then it's doing something like...

```
$usernamePasswordDomain =~ /([^:]*):([^@]*)@(.*)/;
$username = $1;
$password = $2;
$domain = $3;
```

when perhaps it should be...

```
$usernamePasswordDomain =~ /([^:]*):([.*]*)@(.*)/;
$username = $1;
$password = $2;
$domain = $3;
```

eg :

```
echo 'username:passw@rd@home.com' | perl -ane 'print "$_\n"; $_ =~ /([^:]*):(.*)@(.*)/; print join( "\n", $1, $2, $3, "\n" );'
username:passw@rd@home.com

username
passw@rd
home.com
```

as opposed to :

```
echo 'username:passw@rd@home.com' | perl -ane 'print "$_\n"; $_ =~ /([^:]*):([^@]*)@(.*)/; print join( "\n", $1, $2, $3, "\n" );'
username:passw@rd@home.com

username
passw
rd@home.com
```

Any confirm this? If so, please advise where/how to log a bug. I wonder where I can get the source for it, so I can check.

Thanks,

Max.

---

