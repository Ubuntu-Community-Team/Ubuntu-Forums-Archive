---
title: "Problem on repo packages having bug"
date: 2008-07-29
forum: General Help
---

### Post by satimis on 2008-07-29
Hi foilks,


Ubuntu 7.04 server amd64


I have been waiting more than a week for the bug on repo pacakages to be fixed.


There are bugs on the packages to be upgraded, not the problem of broken dependencies;


$ sudo apt-get upgrade```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mysql-server-5.0
The following packages will be upgraded:
  firefox libapache2-mod-php5 libnspr4 libnss3 libpcre3
  linux-image-2.6.20-17-generic linux-libc-dev php-pear php5 php5-cli
  php5-common php5-curl php5-dev php5-gd php5-mhash php5-mysql php5-pspell
  php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl
23 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/41.9MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... Done
Parsing Found/Fixed information... Done
critical bugs of php5 (5.2.1-0ubuntu1.5 -> 5.2.1-0ubuntu1.6) <done>
 #471104 - php5: Please rebuild against up to date timezone data (Fixed: php5/5.2.6-1)
serious bugs of linux-libc-dev (2.6.20-17.36 -> 2.6.20-17.37) <pending>
#435700 - keepalived: FTBFS: conflicting types for 'loff_t'
   Merged with: 434040
Summary:
 php5(1 bug), linux-libc-dev(1 bug)
Are you sure you want to install/upgrade the above packages? [Y/n/?/...]  n

```


So I select "n" to exit```

****************************************************************************
****** Exit with an error by force in order to stop the installation. ******
****************************************************************************
E: Sub-process if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi returned an error code (10)
E: Failure running script if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi

```


I have been googling around discovering threads talking these bugs.  I don't know why Ubuntu 7.04 leaving those buggy packages on the repo.


Any folk has encountered this problem.  Any fix?  TIA


B.R.
satimis

---

