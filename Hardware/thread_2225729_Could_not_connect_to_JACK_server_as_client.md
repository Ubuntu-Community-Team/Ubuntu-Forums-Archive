---
title: "Could not connect to JACK server as client"
date: 2014-05-22
forum: Hardware
---

### Post by Oscar_Frasson on 2014-05-22
When I was configured qjackctl to input Device  to USB Audio Codec (hw:1) ocurred the error:

 [COLOR=#999999]22:04:06.683 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]22:04:06.687 Statistics reset.[/COLOR]
 [COLOR=#cccc99]22:04:06.697 ALSA connection change.[/COLOR]
 [COLOR=#999999]22:04:06.716 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#ff0000]22:04:06.909 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = Arquivo ou diretÃ³rio nÃ£o encontrado
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Cannot connect to server socket err = Arquivo ou diretÃ³rio nÃ£o encontrado
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]22:04:06.942 ALSA connection graph change.[/COLOR]
 Thu May 22 22:04:06 2014: Starting jack server...
 Thu May 22 22:04:06 2014: JACK server starting in realtime mode with priority 10
 Thu May 22 22:04:06 2014: self-connect-mode is "Don't restrict self connect requests"
 Thu May 22 22:04:06 2014: ERROR: Cannot lock down 107335194 byte memory area (Cannot allocate memory)
 Thu May 22 22:04:06 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio1": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio1
 Thu May 22 22:04:06 2014: ERROR: Failed to acquire device name : Audio1 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio1
 Thu May 22 22:04:06 2014: ERROR: Audio device hw:CODEC cannot be acquired...
 Thu May 22 22:04:06 2014: ERROR: Cannot initialize driver
 Thu May 22 22:04:06 2014: ERROR: JackServer::Open failed with -1
 Thu May 22 22:04:06 2014: ERROR: Failed to open server
 Thu May 22 22:04:08 2014: Saving settings to "/home/oz/.config/jack/conf.xml" ...
 [COLOR=#ff0000]22:04:30.157 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = Arquivo ou diretÃ³rio nÃ£o encontrado
 Cannot connect to server request channel
 jack server is not running or cannot be started[ATTACH=CONFIG]253381[/ATTACH]

---

