---
title: "Odd applications launching when I start a section"
date: 2008-09-11
forum: General Help
---

### Post by giuvic on 2008-09-11
Greetings...

I looked for a solution into forums, but I was unable to understand how and why firefox and the console are running when I log in a section...

every time I put my user and password they are launched and I've installed and looked at a numerous softwares for startup and section management, without success.

... any idea?

---

### Post by hwttdz on 2008-09-11
I believe you mean session? 

The two places I would check are system->preferences->sessions and also .bashrc, but I expect it to be the first.  Ask again if you have trouble.

---

### Post by giuvic on 2008-09-11
hmmm...

I've already tryed the session... it does not mention firefox or console.

this folder, .bashrc, where is it?

---

### Post by hwttdz on 2008-09-11
Do you get any strange behavior when you open up a terminal? 

In any case open up a terminal, run "grep firefox *" and "grep firefox .*" post the output of both.

.bashrc is a file which resides in your home directory, it is executed once when you login and again every time you open a terminal.  It's possible that firefox is being opened from inside .bashrc.  BTW the dot out front makes it hidden, if you want to see it when you ls, do ls -A.

---

### Post by giuvic on 2008-09-11
I didn't find the folder.

The first command didn't make anything. The second (grep firefox .*) showed this:

> .bash_history:wget [http://www.google.com.br/search?q=eee+home+ubuntu+hotkey&btnG=Pesquisar&hl=pt-BR&client=firefox-a&rls=com.ubuntu%3Apt-BR%3Aunofficial&hs=YlT&sa=2](http://www.google.com.br/search?q=eee+home+ubuntu+hotkey&btnG=Pesquisar&hl=pt-BR&client=firefox-a&rls=com.ubuntu%3Apt-BR%3Aunofficial&hs=YlT&sa=2)
.bash_history:wget 'http://www.google.com.br/search?q=eee+home+ubuntu+hotkey&btnG=Pesquisar&hl=pt-BR&client=firefox-a&rls=com.ubuntu%3Apt-BR%3Aunofficial&hs=YlT&sa=2'
.bash_history:firefox &
.bash_history:sudo firefox
.bash_history:firefox -ProfileManager
.bash_history:firefox -a asdf
.bash_history:cd .mozilla/firefox/*/
.bash_history:~/.mozilla/firefox
.bash_history:firefox -a asdf
.bash_history:firefox -ProfileManager
.bash_history:firefox -a asdf
.bash_history:firefox -ProfileManager
.bash_history:grep firefox *
.bash_history:grep firefox .*
.recently-used.xbel:  <bookmark href="file:///home/giuvic/.mozilla/firefox/profiles.ini" added="2008-09-03T12:44:38Z" modified="2008-09-03T12:57:20Z" visited="2008-09-03T12:44:38Z">
.recently-used.xbel:          <bookmark:application name="Gerenciador de Arquivos" exec="&apos;firefox&apos;" timestamp="1220484811" count="1"/>
.recently-used.xbel:          <bookmark:application name="Gerenciador de Arquivos" exec="&apos;firefox&apos;" timestamp="1220587003" count="1"/>
.recently-used.xbel:          <bookmark:application name="Gerenciador de Arquivos" exec="&apos;firefox&apos;" timestamp="1220587183" count="1"/>
.recently-used.xbel:  <bookmark href="file:///home/giuvic/.mozilla/firefox/pstw98hz.default/prefs.js" added="2008-09-05T13:56:01Z" modified="2008-09-05T13:56:03Z" visited="2008-09-05T13:56:01Z">
.recently-used.xbel:          <bookmark:application name="Gerenciador de Arquivos" exec="&apos;firefox&apos;" timestamp="1220968463" count="1"/>
.recently-used.xbel:          <bookmark:application name="Gerenciador de Arquivos" exec="&apos;firefox&apos;" timestamp="1221020699" count="1"/>


---

### Post by hwttdz on 2008-09-11
I'm not sure what folder you're talking about.  .bashrc is a file which lives in your home folder, aka. ~, /home/username/ .  

.bash_history tells us what commands have been run from the terminal, I see firefox &, and sudo firefox, which both lauch a firefox, but I assume you did both of those.  

I don't see anything that would launch firefox on every login.  I'm sure someone else will be able to give you some more help.  Sorry.

---

