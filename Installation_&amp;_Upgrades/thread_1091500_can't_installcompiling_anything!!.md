---
title: "can't install/compiling anything!!"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by nid3 on 2009-03-09
hi
I install gcc 3.4.6 and when i type apt-get my console give me answer:
>  apt-get update 
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/apt/methods/http)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
/usr/lib/apt/methods/http: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
apt-get: relocation error: apt-get: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference

And Can You help my heal my ubuntu without reinstalling all system

---

### Post by Neo_The_User on 2009-03-09
Read through the comments and suggestions people made to this bug report.

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/180160](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/180160)

What version of ubuntu are you using? I might be of further assistance if I could get that.

---

### Post by nid3 on 2009-03-09
my ubuntu is 8.10 

i did like them wrote and nothing
> ldconfig -p |grep libstdc++
	libstdc++.so.6 (libc6) => /usr/local/lib/libstdc++.so.6
	libstdc++.so.6 (libc6) => /usr/lib/libstdc++.so.6
	libstdc++.so.5 (libc6) => /usr/lib/libstdc++.so.5
	libstdc++.so (libc6) => /usr/local/lib/libstdc++.so
>  [QUOTE]diff /usr/lib/libstdc++.so.6 /usr/local/lib/libstdc++.so.6
Pliki binarne /usr/lib/libstdc++.so.6 i /usr/local/lib/libstdc++.so.6 si&#281; ró&#380;ni&#261;
the files are diferent[/QUOTE]
> cat /etc/ld.so.conf.d/libc.conf
# libc default configuration
/usr/local/lib

and i add 
> /usr/lib

to this file and nothing, the same problem:/

---

### Post by Neo_The_User on 2009-03-09
Open up a terminal

```

wget http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/libstdc++6_4.3.2-1ubuntu11_i386.deb
sudo dpkg -i libstdc++6_4.3.2-1ubuntu11_i386.deb

```

Also check this out.

```



Hi-

 I found the solution
http://www.linuxdiyf.com/bbs/archiver/tid-68799.htmlwhich is a Chinese
forum. I did as follows:

$ ldconfig -p |grep libstdc++

         libstdc++.so.6 (libc6) => /usr/lib/libstdc++.so.6
         libstdc++.so.6 (libc6) => /usr/local/lib/libstdc++.so.6
$ diff /usr/lib/libstdc++.so.6 /usr/local/lib/libstdc++.so.6
   Binary files /usr/lib/libstdc++.so.6 and /usr/local/lib/libstdc++.so.6
differ
The two files are different which means there are two different versions gcc
in the system? I found a gcc directory under /usr/local

Then : $ cat /etc/ld.so.conf.d/libc.conf
# libc default configuration
/usr/local/lib

I added /usr/lib to the file and then run :
$sudo ldconfig

On Jan 3, 2008 4:43 PM, Jiapeng <email address hidden> wrote:

[...]
> Hi-
> Sorry I don't really understand what you mean. I upgraded from 7.04 to
> 7.10 a couple of months ago and today I upgraded to 8.04. Before upgrading
> to 8.04, the update manager shows my system is up to date.
>
>
> On Jan 3, 2008 3:44 PM, jtholmes <email address hidden> wrote:
>
> >
> > Sorry i asked if you applied all pkg upgrades available for release 7.04
> > that should have been release 7.10
> >
> >
> > ** Changed in: apt (Ubuntu)
> > Sourcepackagename: None => apt
> > Status: In Progress => Incomplete
> >
> > --
> > cannot run apt-get after upgrading to ubuntu 8.04
> > https://bugs.launchpad.net/bugs/180160
> > You received this bug notification because you are a direct subscriber
> > of the bug.
> >
>
>

```

---

### Post by nid3 on 2009-03-09
> pawel@darkstar:~$ wget [http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/libstdc++6_4.3.2-1ubuntu11_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/libstdc++6_4.3.2-1ubuntu11_i386.deb)
--2009-03-09 18:55:59--  [http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/libstdc++6_4.3.2-1ubuntu11_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/libstdc++6_4.3.2-1ubuntu11_i386.deb)
Translacja mirrors.kernel.org... 199.6.1.174, 130.239.17.6
&#321;&#261;czenie si&#281; z mirrors.kernel.org|199.6.1.174|:80... po&#322;&#261;czono.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 200 OK
D&#322;ugo&#347;&#263;: 333266 (325K) [text/plain]
Zapis do: `libstdc++6_4.3.2-1ubuntu11_i386.deb.1'

100%[======================================>] 333.266      287K/s   w 1,1s     

2009-03-09 18:56:00 (287 KB/s) - zapisano `libstdc++6_4.3.2-1ubuntu11_i386.deb.1' [333266/333266]

pawel@darkstar:~$ sudo dpkg -i libstdc++6_4.3.2-1ubuntu11_i386.deb 
(Odczytywanie bazy danych ... 220181 plików i katalogów obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia libstdc++6 4.3.2-1ubuntu11 (wykorzystuj&#261;c libstdc++6_4.3.2-1ubuntu11_i386.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego libstdc++6 ...
Konfigurowanie libstdc++6 (4.3.2-1ubuntu11) ...

Przetwarzanie wyzwalaczy dla libc6...
ldconfig deferred processing now taking place

and the same:/
> pawel@darkstar:~$ apt-get 
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
apt-get: /usr/local/lib/libstdc++.so.6: no version information available (required by /usr/lib/libapt-pkg-libc6.8-6.so.4.6)
apt-get: relocation error: /usr/lib/libapt-pkg-libc6.8-6.so.4.6: symbol _ZSt16__ostream_insertIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_PKS3_i, version GLIBCXX_3.4.9 not defined in file libstdc++.so.6 with link time reference


---

### Post by Neo_The_User on 2009-03-09
NO WONDER! .so means its a devel issue.

wget [http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb)
sudp dpkg -i libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb

Sorry. My mistake. Didn't see the .so

---

### Post by nid3 on 2009-03-09
> sudo dpkg -i libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb
(Odczytywanie bazy danych ... 220181 plików i katalogów obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia libstdc++6-4.3-dev 4.3.2-1ubuntu11 (wykorzystuj&#261;c libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego libstdc++6-4.3-dev ...
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie libstdc++6-4.3-dev:
 libstdc++6-4.3-dev zale&#380;y od g++-4.3 (= 4.3.2-1ubuntu11); jednak&#380;e:
  Wersj&#261; g++-4.3 w systemie jest 4.3.2-1ubuntu12.
dpkg: b&#322;&#261;d przetwarzania libstdc++6-4.3-dev (--install):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 libstdc++6-4.3-dev

and i havnt got libstdc++6-4.3-dev ?i thinked tried to install this lib in libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb ?strange..

---

### Post by Neo_The_User on 2009-03-09
OK can you translate that terminal output in english please?

---

### Post by nid3 on 2009-03-09
sudo dpkg -i libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb
(Odczytywanie bazy danych ... 220181 plików i katalogów obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia libstdc++6-4.3-dev 4.3.2-1ubuntu11 

***Prepering to update libstdc++6-4.3-dev 4.3.2-1ubuntu11*** 

(wykorzystuj&#261;c libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego libstdc++6-4.3-dev ...

***Executing the packet libstdc++6-4.3-dev***


dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie libstdc++6-4.3-dev:

***problems with dependings unables configuring libstdc++6-4.3-dev:** *

libstdc++6-4.3-dev zale&#380;y od g++-4.3 (= 4.3.2-1ubuntu11); jednak&#380;e:
Wersj&#261; g++-4.3 w systemie jest 4.3.2-1ubuntu12.

***In Your system wersion is g++ 4.3***

dpkg: b&#322;&#261;d przetwarzania libstdc++6-4.3-dev (--install):

***error with converting libstdc++6-4.3-dev (--install):** *

problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany

***error with dependings -- not configure***


Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
libstdc++6-4.3-dev 

***errors in converting libstdc++6-4.3-dev** *

grr i'm mad on it....:/

---

### Post by Neo_The_User on 2009-03-09
Don't worry. We are making progress. Don't give up now.

```

wget http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/g++-4.3_4.3.2-1ubuntu11_i386.deb
sudo dpkg -i g++-4.3*
wget http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-4.3/gcc-4.3_4.3.2-1ubuntu11_i386.deb
sudo dpkg -i gcc-4.3*

```

Post output if problems.

You might have to change the order in which the sudo dpkg -i commands are listed in.

---

### Post by nid3 on 2009-03-09
>  sudo dpkg -i g++-4.3*(Odczytywanie bazy danych ... 220181 plików i katalogów obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia g++-4.3 4.3.2-1ubuntu11 (wykorzystuj&#261;c g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego g++-4.3 ...
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie g++-4.3:
 g++-4.3 zale&#380;y od libstdc++6-4.3-dev (= 4.3.2-1ubuntu11); jednak&#380;e:
  Pakiet libstdc++6-4.3-dev nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania g++-4.3 (--install):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Przetwarzanie wyzwalaczy dla man-db...
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 g++-4.3

it wrote errors with compiling ( last 2  lines [I][B]Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 g++-4.3[/B][/I]

and when i download second link 
> sudo dpkg -i gcc-4.3*
dpkg-split: b&#322;&#261;d odczytu gcc-4.3.3: Is a directory
dpkg: b&#322;&#261;d przetwarzania gcc-4.3.3 (--install):
 podproces dpkg-split zwróci&#322; kod b&#322;&#281;du 2
dpkg-deb: "gcc-4.3.3.tar.bz2" nie jest plikiem archiwum Debiana
dpkg: b&#322;&#261;d przetwarzania gcc-4.3.3.tar.bz2 (--install):
 podproces dpkg-deb --control zwróci&#322; kod b&#322;&#281;du 2
(Odczytywanie bazy danych ... 220181 plików i katalogów obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia gcc-4.3 4.3.2-1ubuntu11 (wykorzystuj&#261;c gcc-4.3_4.3.2-1ubuntu11_i386.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego gcc-4.3 ...
Przygotowanie do zast&#261;pienia gcc-4.3 4.3.2-1ubuntu11 (wykorzystuj&#261;c gcc-4.3_4.3.2-1ubuntu11_i386.deb.1) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego gcc-4.3 ...
Przygotowanie do zast&#261;pienia gcc-4.3-base 4.3.2-1ubuntu11 (wykorzystuj&#261;c gcc-4.3-base_4.3.2-1ubuntu11_i386.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego gcc-4.3-base ...
Rozpakowana zosta&#322;a wi&#281;cej ni&#380; jedna kopia pakietu gcc-4.3
 w tym przebiegu!  Konfiguracja odb&#281;dzie si&#281; tylko dla jednej.
Konfigurowanie gcc-4.3-base (4.3.2-1ubuntu11) ...

Konfigurowanie gcc-4.3 (4.3.2-1ubuntu11) ...
Przetwarzanie wyzwalaczy dla man-db...
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 gcc-4.3.3
 gcc-4.3.3.tar.bz2



---

### Post by Neo_The_User on 2009-03-09
I can only read English. Sorry. Can you translate?

---

### Post by nid3 on 2009-03-09
Yes sure i try ( i can't change my language in system to english because my F*** problem...:P)
>  dpkg -i g++-4.3_4.3.2-1ubuntu11_i386.deb 
(Odczytywanie bazy danych ... 220181 plików i katalogów obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia g++-4.3 4.3.2-1ubuntu11 (wykorzystuj&#261;c g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego g++-4.3 ...
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie g++-4.3:
 g++-4.3 zale&#380;y od libstdc++6-4.3-dev (= 4.3.2-1ubuntu11); jednak&#380;e:
  Pakiet libstdc++6-4.3-dev nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania g++-4.3 (--install):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Przetwarzanie wyzwalaczy dla man-db...
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 g++-4.3

Przygotowanie do zast&#261;pienia g++-4.3 4.3.2-1ubuntu11 (wykorzystuj&#261;c g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
[I][B]
Preparing to changing g++-4.3....including g++-4.3_4.3.2-1ubuntu11_i386.deb.[/B][/I]


Rozpakowanie pakietu zast&#281;puj&#261;cego g++-4.3 ...

***Executing packages changing g++-4.3..***


dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie g++-4.3:
 g++-4.3 zale&#380;y od libstdc++6-4.3-dev (= 4.3.2-1ubuntu11); jednak&#380;e:
  Pakiet libstdc++6-4.3-dev nie jest jeszcze skonfigurowany.

***dpkg errors with dependies unable configuring g++-4.3 it is depends from libstdc++6-4.3-dev (= 4.3.2-1ubuntu11);however packet libstdc++6-4.3-dev is not yet configured ***

Przetwarzanie wyzwalaczy dla man-db...
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 g++-4.3

***errors with convert with  g++-4.3***

---

### Post by Neo_The_User on 2009-03-09
sudo dpkg --configure libstdc++6-4.3-dev

This issue seems highly annoying.

---

### Post by nid3 on 2009-03-09
>  dpkg --configure libstdc++6-4.3-dev
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie libstdc++6-4.3-dev:
 libstdc++6-4.3-dev zale&#380;y od g++-4.3 (= 4.3.2-1ubuntu11); jednak&#380;e:
  Pakiet g++-4.3 nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania libstdc++6-4.3-dev (--configure):
 problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 libstdc++6-4.3-dev

errors with dependings...
yes problem is Very annoying.....

---

### Post by Neo_The_User on 2009-03-09
didn't you install g++ by hand already?

---

### Post by nid3 on 2009-03-09
dpkg -i g++-4.3_4.3.2-1ubuntu11_i386.deb

You are asking about this?

---

### Post by Neo_The_User on 2009-03-09
Yes. OK I give up. I can't help. g++ won't install due to libstdc++6-dev but libstdc++6-dev won't install due to g++. I don't know how to help anymore. Try this and if all of these commands give you errors, file a bug for the love of god.

```

sudo dpkg --configure g++ && sudo dpkg --configure libstdc++6-4.3-dev && sudo dpkg --configure libstdc++6-4.3-dev g++ && sudo apt-get install -f

```

---

### Post by nid3 on 2009-03-09
sudo dpkg -i g++-4.3*(Odczytywanie bazy danych ... 220181 plików i katalogów obecnie zainstalowanych.)
Przygotowanie do zast&#261;pienia g++-4.3 4.3.2-1ubuntu11 (wykorzystuj&#261;c g++-4.3_4.3.2-1ubuntu11_i386.deb) ...
Rozpakowanie pakietu zast&#281;puj&#261;cego g++-4.3 ...
dpkg: problemy z zale&#380;no&#347;ciami uniemo&#380;liwiaj&#261; skonfigurowanie g++-4.3:
g++-4.3 zale&#380;y od libstdc++6-4.3-dev (= 4.3.2-1ubuntu11); jednak&#380;e:
Pakiet libstdc++6-4.3-dev nie jest jeszcze skonfigurowany.
dpkg: b&#322;&#261;d przetwarzania g++-4.3 (--install):
problemy z zale&#380;no&#347;ciami - pozostawiony nieskonfigurowany
Przetwarzanie wyzwalaczy dla man-db...
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
g++-4.3
it wrote errors with compiling ( last 2 lines Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
g++-4.3





>  sudo dpkg --configure g++ && sudo dpkg --configure libstdc++6-4.3-dev && sudo dpkg --configure libstdc++6-4.3-dev g++ && sudo apt-get install -f
dpkg: b&#322;&#261;d przetwarzania g++ (--configure):
 pakiet g++ jest ju&#380; zainstalowany i skonfigurowany  // it wrote that packet is instaled and configured 
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:// and in this line : errors with compiling g++
 g++


---

### Post by Neo_The_User on 2009-03-09
Go send a few ubuntu forum staff a link to your thread as a private message or as a vistor message and let them check it out. I can't help. I don't know this stuff.

---

