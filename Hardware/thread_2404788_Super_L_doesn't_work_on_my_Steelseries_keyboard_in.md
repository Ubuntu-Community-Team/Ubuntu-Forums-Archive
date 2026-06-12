---
title: "Super L doesn't work on my Steelseries keyboard in Ubuntu"
date: 2018-10-28
forum: Hardware
---

### Post by edx92 on 2018-10-28
Hello, I'm wondering how to configure my keyboard layout in Ubuntu.
Release: Ubuntu 18.04
Keyboard model: Steelseries  6gv2 (US layout)

I configured /etc/default/keyboard like so:
```

XKBLAYOUT=us
XKBVARIANT=,
BACKSPACE=guess

```

If I use sudo showkey, when I press Super L no keycode appear, so I can't find a way to configure it.
Instead, Super R work properly.
Can anyone help me with complete step to set Super L? Thanks

---

### Post by edx92 on 2018-10-30
up

---

### Post by edx92 on 2018-10-31
up

---

### Post by ubu69 on 2018-10-31
Editing configuration files by hand can be a tricky prospect. May I suggest running:

```
sudo dpkg-reconfigure keyboard-configuration
```

Try choosing "Generic 105-key PC (intl.)" and see how it goes.

You may find [this thread](https://askubuntu.com/questions/342066/how-to-permanently-configure-keyboard) on askubuntu helpful.

---

### Post by edx92 on 2018-11-02
Thank you for the answer. I tried what you said, but it doesn't worked. The problem is that Super L is not recognized at all.

    ```
edx@edx-Kingston:~$ sudo showkey
    kb mode was ?UNKNOWN?
    [ if you are trying this under X, it might not work
    since the X server is also reading /dev/console ]

    press any key (program terminates 10s after last keypress)...
    keycode  28 release
    keycode 126 press
    keycode 126 release
```

keycode 126 is Super R, super L do nothing...

---

### Post by edx92 on 2018-11-02
I found that no software solution is possible. The only way to do it is with physical bridge, opening the keyboard and soldering 2 cables between Super L and Super R. Ok, not so practical, I will use Ctrl instead ):P

---

