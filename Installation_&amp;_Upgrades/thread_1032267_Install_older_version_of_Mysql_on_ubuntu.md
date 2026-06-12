---
title: "Install older version of Mysql on ubuntu"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by nel636 on 2009-01-06
Hi guys,

Was hoping someone could help me witha mysql query??

Basically im trying to install opsview for network monitoring. anyway after over coming dozens of issues i have opsview installed but when i tried and import flow data into mysql i get errors regarding the SQL syntax of the perl script provided with Flavio (the netflow collector).

Currently im using ubuntu desktop 8.04 and "thought" the script would be ok with the latest version of mysql5. Since im running into SQL syntax issues i wanted to downgrade to an older version of mysql to see if it works on a previous version. The one in the write up uses mysql 2.1013. However when i try to install mysql using apt-get it installs the latest version.

So ive googled and found the mysql v2 mentioned - which ive downloaded. but how do i go about manually installing the files in the .tar folder? and when i do how do i prevent apt-get from updating mysql in the future?

Ive looked through google and cant find anything concrete but will keep looking.

Lastly, does anyone think the syntax issues could be related to the new version of mysql?

I would really like to get this working cos we cant afford a payed for solution at the moment!! and i need statistics haha!!

Thanks Guys

---

### Post by infamous-online on 2009-01-06
perhaps you should try and build the mysql server yourself from a tar file and see if that helps. mysql 2 has been forgotten about years ago, so perhaps it could be your code. However, the syntax really didn't change that much, so if you could post some of the code and make it bold so we'll know it's the code.

---

### Post by nel636 on 2009-01-07
Hi,

Thanks for the reply!

Here is part of the SQL code, i have highlighted the the code in bold to identify the syntax issue:

```
$statement = "DELETE from $weekTable where **starttime >= $since and endtime <= $to"**;
$sth = $dbh->prepare($statement);
$sth->execute or die "Unable to execute query:$dbh->err, $dbh->errstr\n";
$sth->finish;
$statement = "DELETE from $monthTable where **starttime >= $since and endtime <= $to"**;
$sth = $dbh->prepare($statement);
$sth->execute or die "Unable to execute query:$dbh->err, $dbh->errstr\n";
$sth->finish;
$statement = "DELETE from $yearTable where **starttime >= $since and endtime <= $to"**;
$sth = $dbh->prepare($statement);
$sth->execute or die "Unable to execute query:$dbh->err, $dbh->errstr\n";
$sth->finish;
```

Its the syntax above where it states starttime >= $since and endtime <= $to....

Like i said, this is part of a bigger perl script which came with the software.

Thanks for taking the time to look.

---

### Post by nel636 on 2009-01-07
Just to let you know, this is the error output i get:

./netflow_aggregate.pl 2009 1 7
Table: 2009_1_7
Week: 1
WeekTable: W2009_1
MonthTable: M2009_1
YearTable: Y2009
DBD::mysql::st execute failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'and endtime <=' at line 1 at ./netflow_aggregate.pl line 114.
Unable to execute query:DBI::db=HASH(0x82e0658)->err, DBI::db=HASH(0x82e0658)->errstr

---

### Post by sabin on 2009-01-15
I have the same issue. did you manage to solve that problem?

For further projects I need to make that work some way...

greets

---

