---
title: "[SOLVED] Annoying characters in terminal"
date: 2008-07-24
forum: General Help
---

### Post by Dylock on 2008-07-24
This has been something I've lived with and have finally decided to fix all the little things that have bothered me on my machine. One is those 'crappy' characters that show up in the terminal. Sometimes this makes applications unusable, for example finch looks like a mess and sometimes its hard to read certain man pages.

You can see a few of these in the SS I attached(there are very few on this man page, go figure).

I have my language set to english(US).
The output of env gives me en_US.UTF-8 for LANG

Any suggestions?

---

### Post by pauper on 2008-07-24
Do you experience the same problem on TTY?

Please, attach the output of:

```
infocmp $TERM
```

---

### Post by Dylock on 2008-07-24
```
dylock@dybox:~$ infocmp $term
#       Reconstructed via infocmp from file: /lib/terminfo/r/rxvt
rxvt|rxvt terminal emulator (X Window System), 
        am, bce, eo, km, mir, msgr, xenl, xon, 
        colors#8, cols#80, it#8, lines#24, ncv@, pairs#64, 
        acsc=``aaffggjjkkllmmnnooppqqrrssttuuvvwwxxyyzz{{||}}~~, 
        bel=^G, blink=\E[5m, bold=\E[1m, civis=\E[?25l, 
        clear=\E[H\E[2J, cnorm=\E[?25h, cr=^M, 
        csr=\E[%i%p1%d;%p2%dr, cub=\E[%p1%dD, cub1=^H, 
        cud=\E[%p1%dB, cud1=^J, cuf=\E[%p1%dC, cuf1=\E[C, 
        cup=\E[%i%p1%d;%p2%dH, cuu=\E[%p1%dA, cuu1=\E[A, 
        dl=\E[%p1%dM, dl1=\E[M, ed=\E[J, el=\E[K, el1=\E[1K, 
        enacs=\E(B\E)0, flash=\E[?5h\E[?5l, home=\E[H, 
        hpa=\E[%i%p1%dG, ht=^I, hts=\EH, ich=\E[%p1%d@, ich1=\E[@, 
        il=\E[%p1%dL, il1=\E[L, ind=^J, is1=\E[?47l\E=\E[?1l, 
        is2=\E[r\E[m\E[2J\E[H\E[?7h\E[?1;3;4;6l\E[4l, 
        kDC=\E[3$, kEND=\E[8$, kHOM=\E[7$, kLFT=\E[d, kNXT=\E[6$, 
        kPRV=\E[5$, kRIT=\E[c, ka1=\EOw, ka3=\EOy, kb2=\EOu, 
        kbs=\177, kc1=\EOq, kc3=\EOs, kcbt=\E[Z, kcub1=\E[D, 
        kcud1=\E[B, kcuf1=\E[C, kcuu1=\E[A, kdch1=\E[3~, 
        kel=\E[8\^, kend=\E[8~, kent=\EOM, kf1=\E[11~, kf10=\E[21~, 
        kf11=\E[23~, kf12=\E[24~, kf13=\E[25~, kf14=\E[26~, 
        kf15=\E[28~, kf16=\E[29~, kf17=\E[31~, kf18=\E[32~, 
        kf19=\E[33~, kf2=\E[12~, kf20=\E[34~, kf21=\E[23$, 
        kf22=\E[24$, kf23=\E[11\^, kf24=\E[12\^, kf25=\E[13\^, 
        kf26=\E[14\^, kf27=\E[15\^, kf28=\E[17\^, kf29=\E[18\^, 
        kf3=\E[13~, kf30=\E[19\^, kf31=\E[20\^, kf32=\E[21\^, 
        kf33=\E[23\^, kf34=\E[24\^, kf35=\E[25\^, kf36=\E[26\^, 
        kf37=\E[28\^, kf38=\E[29\^, kf39=\E[31\^, kf4=\E[14~, 
        kf40=\E[32\^, kf41=\E[33\^, kf42=\E[34\^, kf43=\E[23@, 
        kf44=\E[24@, kf5=\E[15~, kf6=\E[17~, kf7=\E[18~, 
        kf8=\E[19~, kf9=\E[20~, kfnd=\E[1~, khome=\E[7~, 
        kich1=\E[2~, kmous=\E[M, knp=\E[6~, kpp=\E[5~, kslt=\E[4~, 
        op=\E[39;49m, rc=\E8, rev=\E[7m, ri=\EM, rmacs=^O, 
        rmcup=\E[2J\E[?47l\E8, rmir=\E[4l, rmkx=\E>, rmso=\E[27m, 
        rmul=\E[24m, 
        rs1=\E>\E[1;3;4;5;6l\E[?7h\E[m\E[r\E[2J\E[H, 
        rs2=\E[r\E[m\E[2J\E[H\E[?7h\E[?1;3;4;6l\E[4l\E=\E[?1000l\E[?25h, 
        s0ds=\E(B, s1ds=\E(0, sc=\E7, setab=\E[4%p1%dm, 
        setaf=\E[3%p1%dm, 
        sgr=\E[0%?%p6%t;1%;%?%p2%t;4%;%?%p1%p3%|%t;7%;%?%p4%t;5%;m%?%p9%t\016%e\           017%;, 
        sgr0=\E[m\017, smacs=^N, smcup=\E7\E[?47h, smir=\E[4h, 
        smkx=\E=, smso=\E[7m, smul=\E[4m, tbc=\E[3g, 
        vpa=\E[%i%p1%dd, 

```

---

### Post by pauper on 2008-07-24
Check line #40.

> ```
...\016%e\           017%;,
```

Is it a copy&paste error or you have the same output in terminal as well?
There must be no spaces after "\".

Please, attach the output:

```
locale
grep Xkb /etc/X11/xorg.conf
cat /etc/default/locale
grep -vE '(^[[:space:]]*#|^[[:space:]]*$)' /etc/default/console-setup
env | grep -E '(*LANG*|*LOCALE*)'
```

---

### Post by Dylock on 2008-07-24
> **pauper said:**
> Check line #40.



Is it a copy&paste error or you have the same output in terminal as well?
There must be no spaces after "\".



This appears to just be a copy paste error.

locale
```

dylock@dybox:~$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

grep Xkb /etc/X11/xorg.conf
```

dylock@dybox:~$ grep Xkb /etc/X11/xorg.conf
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"

```

cat /etc/default/locale
```

dylock@dybox:~$ cat /etc/default/locale 
LANG="en_US.UTF-8"

```

grep -vE '(^[[:space:]]*#|^[[:space:]]*$)' /etc/default/console-setup
```

dylock@dybox:~$ grep -vE '(^[[:space:]]*#|^[[:space:]]*$)' /etc/default/console-setup 
VERBOSE_OUTPUT=no
ACTIVE_CONSOLES="/dev/tty[1-6]"
CHARMAP="UTF-8"
CODESET="Uni1"
FONTFACE="Fixed"
FONTSIZE="16"
XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""
BOOTTIME_KMAP_MD5="aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa"

```

env | grep -E '(*LANG*|*LOCALE*)'
```

dylock@dybox:~$ env | grep -E '(*LANG*|*LOCALE*)'
LANG=en_US.UTF-8

```

---

### Post by pauper on 2008-07-24
1) > ```
dylock@dybox:~$ env | grep -E '(*LANG*|*LOCALE*)'
LANG=en_US.UTF-8
```

Mine output has three entries:

```
:~$ env | grep -E '(*LANG*|*LOCALE*)'
LANG=en_US.UTF-8
GDM_LANG=en_US.UTF-8
XTERM_LOCALE=en_US.UTF-8
```

Note: $TERM=xterm in my case, yours is rxvt. Recheck it by issuing

```
echo $TERM
```

I suggest you to try:

```
export GDM_LANG=en_US.UTF-8
export RXVT_LOCALE=en_US.UTF-8
bash
```

And view some man pages that give you garbled characters.

If it works than make this change permanent:

```
echo "
> export GDM_LANG=en_US.UTF-8
> export RXVT_LOCALE=en_US.UTF-8" >> ~/.bashrc
bash
```

2) CODESET="Uni2" in mine /etc/default/console-setup. You may try to change that as well.

The rest is same.

---

### Post by Dylock on 2008-07-24
After learning a lot about locale from pauper's posts :) I found that aterm doesn't have good support for locales. So I added ```
export LANG=C
``` to my .bashrc and rebooted. Things now seem to look fine, I can have a readable finch, and man pages seem to be fine.

Thanks to pauper, I learned a lot from you :)

future aterm users: set your LANG=C to fix character problems.

---

