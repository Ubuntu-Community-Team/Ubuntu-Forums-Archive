---
title: "[SOLVED] MySQL with Perl and Apache"
date: 2008-11-15
forum: General Help
---

### Post by Wickd on 2008-11-15
Hi there

I have been looking for a way to query a mysql database. But everytime I compile the code I get the following error:

Can't locate mysql.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at Tryit.pl line 3.
BEGIN failed--compilation aborted at Tryit.pl line 3

So how do I edit the @INC file? Also is there any good howtos on the net on Perl, mysql and apache on the net? I have been searching, but I cant find anything except LAMP. I would like to attempt this myself

Thanks

---

### Post by loell on 2008-11-15
you need to install [libdbd-mysql-perl]("apt:libdbd-mysql-perl") package.

---

### Post by iponeverything on 2008-11-15
you could also do:

```
sudo apt-get build-dep mysql-server
```

that should get all of the build dependencies take care of.

---

### Post by unutbu on 2008-11-15
For documentation on how to use MySQL with Perl, type```


perldoc DBI
```

in a terminal. There is a lot of excellent perl documentation already in your computer which is accessible through perldoc. Type "perldoc perldoc" to learn more.

Here is the basic code one would use to access a mysql database using perl:

[PHP]#!/usr/bin/perl
use strict;
use warnings;
use DBI;

my $username='user';
my $pass='abracadabra';
my $db='userdb';
my $dbh = DBI->connect( "dbi:mysql:$db", $username, $pass, { 'PrintError' => 1, 'RaiseError' => 1 } );
my $sql='select * from table where id=?';
my $sql_arg=1;
my $sql_handle=$dbh->prepare($sql);
$sql_handle->execute($sql_arg);
my @data;
while (@data=$sql_handle->fetchrow_array()) {
    print join("\n",@data)
}
[/PHP]

If this doesn't help, please post your code.

---

### Post by Wickd on 2008-11-15
Thanks for all the help thus far. Unutbu, I have basically copied your code and made a couple of amendments. It seems to connect fine, but I get an error:

Here is my Code:

#!/usr/lib/perl5/DBD

use strict;
use warnings;
use DBI;

my $username='root';
my $pass='crazzee';
my $db='CONTACTS';
my $dbh = DBI->connect( "dbi:mysql:$db", $username, $pass, { 'PrintError' => 1, 'RaiseError' => 1 } );

my $sql='select * from NEW;';
my $sql_arg=0;
my $sql_handle=$dbh->prepare($sql);
$sql_handle->execute($sql_arg);
my @data;

while (@data=$sql_handle->fetchrow_array()) {
    print join("\n",@data)
}

And here is my error:

st execute failed: called with 1 bind variables when 0 are needed at Tryit.pl line 15.
DBD::mysql::st execute failed: called with 1 bind variables when 0 are needed at Tryit.pl line 15.

Maybe I changed something I should not?

Thanks

---

### Post by unutbu on 2008-11-15
The command
```

$sql_handle->execute($sql_arg);

```
injects $sql_arg into the sql statement wherever a question mark (?) is found. In your case, 'select * from NEW', has no question marks, so there is no need for any additional argument. So try
```

$sql_handle->execute();

```
instead.

The error
```

DBD::mysql::st execute failed: called with 1 bind variables when 0 are needed at Tryit.pl line 15.
```
is saying that you fed the execute command 1 variable ($sql_arg) when 0 are needed.

The idea is you prepare an sql statement once, and can potentially execute it many times with different arguments. 

For example, if you write

```
my $sql='insert into NEW (field1,field2) values (?,?)';
my $sql_handle=$dbh->prepare($sql);
```

the you can use the same $sql_handle many times like this:

```
foreach my ($val1,$val2) (@data) {
    $sql_handle->execute($val1,$val2);
}
```

---

### Post by Wickd on 2008-11-15
> **unutbu said:**
> The command
```

$sql_handle->execute($sql_arg);

```
injects $sql_arg into the sql statement wherever a question mark (?) is found. In your case, 'select * from NEW', has no question marks, so there is no need for any additional argument. So try
```

$sql_handle->execute();

```
instead.

The error
```

DBD::mysql::st execute failed: called with 1 bind variables when 0 are needed at Tryit.pl line 15.
```
is saying that you fed the execute command 1 variable ($sql_arg) when 0 are needed.

The idea is you prepare an sql statement once, and can potentially execute it many times with different arguments. 

For example, if you write

```
my $sql='insert into NEW (field1,field2) values (?,?)';
my $sql_handle=$dbh->prepare($sql);
```

the you can use the same $sql_handle many times like this:

```
foreach my ($val1,$val2) (@data) {
    $sql_handle->execute($val1,$val2);
}
```

Kewl thanks, that sorted the problem. Still gotta lot to learn. Have just recently started learning Perl.

Thanks again mfor all the help

Chz

---

### Post by CirruZZ on 2009-02-12
> **unutbu said:**
> For documentation on how to use MySQL with Perl, type```


perldoc DBI
```

in a terminal. There is a lot of excellent perl documentation already in your computer which is accessible through perldoc. Type "perldoc perldoc" to learn more.

Here is the basic code one would use to access a mysql database using perl:

[PHP]#!/usr/bin/perl
use strict;
use warnings;
use DBI;

my $username='user';
my $pass='abracadabra';
my $db='userdb';
my $dbh = DBI->connect( "dbi:mysql:$db", $username, $pass, { 'PrintError' => 1, 'RaiseError' => 1 } );
my $sql='select * from table where id=?';
my $sql_arg=1;
my $sql_handle=$dbh->prepare($sql);
$sql_handle->execute($sql_arg);
my @data;
while (@data=$sql_handle->fetchrow_array()) {
    print join("\n",@data)
}
[/PHP]

If this doesn't help, please post your code.


I just want to say Tanks for a great piece  of code! That helped me much getting PERL and MySQL working together.

---

