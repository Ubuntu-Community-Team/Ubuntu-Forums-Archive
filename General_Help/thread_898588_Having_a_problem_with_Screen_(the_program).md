---
title: "Having a problem with Screen (the program)"
date: 2008-08-23
forum: General Help
---

### Post by MasterXandrex on 2008-08-23
All, I am having a problem with screen. I use an encrypted drive and I want screen to start a program that will write to a folder in the drive. However, if the drive is not mounted I do not want the program started as it will place files outside of the file system of the encrypted drive (on /). I'm using the following script (sanatized):

```

if [ -a /media/crypt1/folder ]; then
        program -o encryption=require_RC4,directory="/media/crypt1/folder"
fi
vim   # This was added for debugging purposes as screen was starting nothing

```

Here is my .screenrc:

```
hardstatus alwayslastline
hardstatus string '%{= kG}[ %{G}%H %{g}][%= %{=kw}%?%-Lw%?%{r}(%{W}%n*%f%t%?(%u)%?%{r})%{w}%?%+Lw%?%?%= %{g}][%{B}%Y-%m-%d %{W}%c %{g}]'
# Default screens
screen -t Shell1        1
screen -t Shell2        2
screen -t RTorrent      3       /home/xandrex/scripts/r_start

```

If I run the script from the terminal or even the virtual terminal in screen, it works perfectly; however, inside screen I get VIM. Does anyone know what's going on...? I looked at env and both SHELL and PATH are the same.

Please, any ideas would be helpful,

Xan

---

### Post by LateNiteTV on 2008-08-23
what do u mean by "i get VIM"?

---

### Post by MasterXandrex on 2008-08-23
If you look at the script that I am running, ir first does the check on the folder existance and then (if true) runs a program. After that I have the line "vim" that will start VIM either way (just added for debugging). If the conditioal is successful I should get the first program and then when I exit the second, but in screen I just get VIM, meaning the conditional always fails, even when it shouldn't.

Xan

---

