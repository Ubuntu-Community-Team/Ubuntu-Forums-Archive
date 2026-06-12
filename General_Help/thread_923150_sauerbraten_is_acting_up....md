---
title: "sauerbraten is acting up..."
date: 2008-09-18
forum: General Help
---

### Post by jmd9qs on 2008-09-18
hey all,

just installed sauerbraten.... freakin' awsome game! however, after i played it for the first time for about 5 min, i realized that there is no sound during gameplay. i quit the game to search the forums, and now when i try to run it, it freezes x up... still no sound as well. here is the error message:

```

jmd9qs@jmd9qs-desktop:~/Desktop/sauerbraten$ sudo ./sauerbraten_unix
Using home directory: /home/jmd9qs/.sauerbraten
init: sdl
[U]ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
init: enet[/U]
init: video: mode
init: video: misc
init: gl
Renderer: GeForce 6150SE nForce 430/PCI/SSE2/3DNOW! (NVIDIA Corporation)
Driver: 2.1.2 NVIDIA 169.12
Rendering using the OpenGL 1.5 GLSL shader path.
init: console
init: gl: effects
init: world
init: sound
_sound init failed (SDL_mixer): No available audio device_
init: cfg
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.1 seconds)
Mining Station by metlslime
game mode is ffa/default


```

anyone know what i can do to fix this? also, i am a newbie, so if it involves anything "technical" please elaborate....

thanks

** Just noticed that when x freezes up, i can move the player around w/ the "wasd" keys, but the mouse doesn't work...

---

### Post by jmd9qs on 2008-09-22
bump bump bump...

---

### Post by noerrorsfound on 2008-09-30
You may have the problem where only one application can use sound at the same time. Try closing your browser and any other applications and then running it. That shouldn't freeze anything up, though.

Posts that aren't responded to are listed at Forum Tools > Unanswered Posts (found on the list of posts in any section). [http://ubuntuforums.org/search.php?do=process&replyless=1&replylimit=0&forumchoice[]=331&dontcache=1](http://ubuntuforums.org/search.php?do=process&replyless=1&replylimit=0&forumchoice[]=331&dontcache=1)

Bumping your post takes it off that list which could decrease your chances of getting help from the people who check unanswered posts.

Back to your problem, you may need to go to the [official Sauerbraten forum](http://cubeengine.com/forum.php4) and ask for help there. I think it's more likely someone knows how to solve your problem on that forum than here.

---

