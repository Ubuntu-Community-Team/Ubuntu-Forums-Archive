---
title: "Need some ./configure help"
date: 2008-10-18
forum: General Help
---

### Post by opothehippo on 2008-10-18
I've got a problem, but I know it can be fixed just real quick. I am installing entertainer, and am far from a person that can install source easily. So I looked up the guides on the internet, searching all around, but I couldn't find anything that would help me.

This is what I'm doing to get to the configure step. I used [this](http://howto.wired.com/wiki/Compile_Software_from_Source_Code) guide to help me because this is my first time compiling from source.

```
chris@awesometop:~$ cd ~/Source
chris@awesometop:~/Source$ tar -xzvf entertainer-0.1.tar.gz
entertainer-0.1/
entertainer-0.1/LICENCE
entertainer-0.1/docs/
entertainer-0.1/docs/preferences_gui.tex
entertainer-0.1/docs/diagrams/
entertainer-0.1/docs/diagrams/Backend/
entertainer-0.1/docs/diagrams/Backend/backend_class_diagram.png
entertainer-0.1/docs/diagrams/Backend/backend_hi_level_arch.dia
entertainer-0.1/docs/diagrams/Backend/backend_class_diagram_new.dia
entertainer-0.1/docs/diagrams/Backend/high_level.png
entertainer-0.1/docs/diagrams/Backend/Backend_classes_in_detail.dia
entertainer-0.1/docs/diagrams/Backend/backend_class_diagram.dia
entertainer-0.1/docs/diagrams/Backend/media_indexer_class_diagram.dia
entertainer-0.1/docs/diagrams/Backend/Backend_classes_in_detail.png
entertainer-0.1/docs/diagrams/Backend/backend_class_diagram_new.png
entertainer-0.1/docs/diagrams/Backend/image_cache_sequece_diagram.dia
entertainer-0.1/docs/diagrams/Backend/media_indexer_class_diagram.png
entertainer-0.1/docs/diagrams/Backend/image_cache_sequece_diagram.png
entertainer-0.1/docs/diagrams/ER/
entertainer-0.1/docs/diagrams/ER/feed_library_er.png
entertainer-0.1/docs/diagrams/ER/feed_library_er.dia
entertainer-0.1/docs/diagrams/ER/image_library_er.png
entertainer-0.1/docs/diagrams/ER/image_library_er.dia
entertainer-0.1/docs/diagrams/ER/music_library_er.dia
entertainer-0.1/docs/diagrams/ER/music_library_er.png
entertainer-0.1/docs/diagrams/Frontend/
entertainer-0.1/docs/diagrams/Frontend/frontend_class_diagram_high.dia
entertainer-0.1/docs/diagrams/Frontend/medialibrary/
entertainer-0.1/docs/diagrams/Frontend/medialibrary/video_library.dia
entertainer-0.1/docs/diagrams/Frontend/medialibrary/feed_library.png
entertainer-0.1/docs/diagrams/Frontend/medialibrary/video_library.png
entertainer-0.1/docs/diagrams/Frontend/medialibrary/image_library.png
entertainer-0.1/docs/diagrams/Frontend/medialibrary/music_library.png
entertainer-0.1/docs/diagrams/Frontend/medialibrary/image_library.dia
entertainer-0.1/docs/diagrams/Frontend/medialibrary/music_library.dia
entertainer-0.1/docs/diagrams/Frontend/medialibrary/feed_library.dia
entertainer-0.1/docs/diagrams/Frontend/gui.dia
entertainer-0.1/docs/diagrams/Frontend/frontend_class_diagram_high.png
entertainer-0.1/docs/diagrams/Frontend/frontend_class_diagram.dia
entertainer-0.1/docs/diagrams/Frontend/weather.dia
entertainer-0.1/docs/diagrams/Frontend/frontend_class_diagram.png
entertainer-0.1/docs/diagrams/gui_layers.png
entertainer-0.1/docs/diagrams/high-level-diagram.png
entertainer-0.1/docs/diagrams/high-level-diagram.dia
entertainer-0.1/docs/cache.tex
entertainer-0.1/docs/user_guide.tex
entertainer-0.1/docs/developer_documentation.tex
entertainer-0.1/docs/developer_documentation.aux
entertainer-0.1/docs/frontend_architecture.tex
entertainer-0.1/docs/message_bus_notifier.tex
entertainer-0.1/docs/developer_documentation.toc
entertainer-0.1/docs/developer_documentation.pdf
entertainer-0.1/docs/high_level_architecture.tex
entertainer-0.1/docs/gui.tex
entertainer-0.1/docs/components.tex
entertainer-0.1/docs/content_management_gui.tex
entertainer-0.1/docs/introduction.tex
entertainer-0.1/docs/backend_core.tex
entertainer-0.1/DEPENDENCIES
entertainer-0.1/HACKING
entertainer-0.1/cfg/
entertainer-0.1/cfg/data/
entertainer-0.1/cfg/data/icons/
entertainer-0.1/cfg/data/icons/24x24/
entertainer-0.1/cfg/data/icons/24x24/entertainer.png
entertainer-0.1/cfg/data/icons/scalable/
entertainer-0.1/cfg/data/icons/scalable/entertainer.svg
entertainer-0.1/cfg/cache/
entertainer-0.1/cfg/cache/movie_art/
entertainer-0.1/cfg/cache/thumbnails/
entertainer-0.1/cfg/cache/thumbnails/image/
entertainer-0.1/cfg/cache/thumbnails/recording/
entertainer-0.1/cfg/cache/thumbnails/video/
entertainer-0.1/cfg/cache/album_art/
entertainer-0.1/cfg/cache/album_art/small/
entertainer-0.1/cfg/content.conf
entertainer-0.1/cfg/themes/
entertainer-0.1/cfg/themes/Black/
entertainer-0.1/cfg/themes/Black/thumbnail.png
entertainer-0.1/cfg/themes/Black/theme.conf
entertainer-0.1/cfg/themes/Black/images/
entertainer-0.1/cfg/themes/Black/images/weather/
entertainer-0.1/cfg/themes/Black/images/weather/rain.png
entertainer-0.1/cfg/themes/Black/images/weather/lightning.png
entertainer-0.1/cfg/themes/Black/images/weather/ice.png
entertainer-0.1/cfg/themes/Black/images/weather/rain_chance.png
entertainer-0.1/cfg/themes/Black/images/weather/fog.png
entertainer-0.1/cfg/themes/Black/images/weather/sun_clouds.png
entertainer-0.1/cfg/themes/Black/images/weather/sun.png
entertainer-0.1/cfg/themes/Black/images/weather/clouds.png
entertainer-0.1/cfg/themes/Black/images/weather/na.png
entertainer-0.1/cfg/themes/Black/images/weather/sun_mostly.png
entertainer-0.1/cfg/themes/Black/images/weather/snow.png
entertainer-0.1/cfg/themes/Black/images/menuitem_bg.png
entertainer-0.1/cfg/themes/Black/images/selector.png
entertainer-0.1/cfg/themes/Black/images/zoom_aspect_ratio.png
entertainer-0.1/cfg/themes/Black/images/menu_overlay.png
entertainer-0.1/cfg/themes/Black/images/native_aspect_ratio.png
entertainer-0.1/cfg/themes/Black/images/star.png
entertainer-0.1/cfg/themes/Black/images/selector_glow.png
entertainer-0.1/cfg/themes/Black/images/star2.png
entertainer-0.1/cfg/themes/Black/images/menu_overlay_LARGE.png
entertainer-0.1/cfg/themes/Black/images/warning_icon.png
entertainer-0.1/cfg/themes/Black/images/new.png
entertainer-0.1/cfg/themes/Black/images/rss_icon.png
entertainer-0.1/cfg/themes/Black/images/default_movie_art.png
entertainer-0.1/cfg/themes/Black/images/disc.png
entertainer-0.1/cfg/themes/Black/images/default_album_art.png
entertainer-0.1/cfg/themes/Black/images/widescreen_aspect_ratio.png
entertainer-0.1/cfg/themes/Black/images/compromise_aspect_ratio.png
entertainer-0.1/cfg/themes/Default/
entertainer-0.1/cfg/themes/Default/thumbnail.png
entertainer-0.1/cfg/themes/Default/theme.conf
entertainer-0.1/cfg/themes/Default/images/
entertainer-0.1/cfg/themes/Default/images/weather/
entertainer-0.1/cfg/themes/Default/images/weather/rain.png
entertainer-0.1/cfg/themes/Default/images/weather/lightning.png
entertainer-0.1/cfg/themes/Default/images/weather/ice.png
entertainer-0.1/cfg/themes/Default/images/weather/rain_chance.png
entertainer-0.1/cfg/themes/Default/images/weather/fog.png
entertainer-0.1/cfg/themes/Default/images/weather/sun_clouds.png
entertainer-0.1/cfg/themes/Default/images/weather/sun.png
entertainer-0.1/cfg/themes/Default/images/weather/clouds.png
entertainer-0.1/cfg/themes/Default/images/weather/na.png
entertainer-0.1/cfg/themes/Default/images/weather/sun_mostly.png
entertainer-0.1/cfg/themes/Default/images/weather/snow.png
entertainer-0.1/cfg/themes/Default/images/menuitem_bg.png
entertainer-0.1/cfg/themes/Default/images/selector.png
entertainer-0.1/cfg/themes/Default/images/menu_overlay2.png
entertainer-0.1/cfg/themes/Default/images/media-skip-backward.png
entertainer-0.1/cfg/themes/Default/images/media-playback-pause.png
entertainer-0.1/cfg/themes/Default/images/zoom_aspect_ratio.png
entertainer-0.1/cfg/themes/Default/images/menu_overlay.png
entertainer-0.1/cfg/themes/Default/images/media-playback-stop.png
entertainer-0.1/cfg/themes/Default/images/native_aspect_ratio.png
entertainer-0.1/cfg/themes/Default/images/star.png
entertainer-0.1/cfg/themes/Default/images/selector_glow.png
entertainer-0.1/cfg/themes/Default/images/star2.png
entertainer-0.1/cfg/themes/Default/images/media-seek-backward.png
entertainer-0.1/cfg/themes/Default/images/warning_icon.png
entertainer-0.1/cfg/themes/Default/images/new.png
entertainer-0.1/cfg/themes/Default/images/media-skip-forward.png
entertainer-0.1/cfg/themes/Default/images/media-playback-start.png
entertainer-0.1/cfg/themes/Default/images/media-eject.png


entertainer-0.1/cfg/themes/Default/images/rss_icon.png
entertainer-0.1/cfg/themes/Default/images/media-seek-forward.png
entertainer-0.1/cfg/themes/Default/images/default_movie_art.png
entertainer-0.1/cfg/themes/Default/images/disc.png
entertainer-0.1/cfg/themes/Default/images/default_album_art.png
entertainer-0.1/cfg/themes/Default/images/widescreen_aspect_ratio.png
entertainer-0.1/cfg/themes/Default/images/compromise_aspect_ratio.png
entertainer-0.1/cfg/preferences.conf
entertainer-0.1/src/
entertainer-0.1/src/entertainer-tray-icon.py
entertainer-0.1/src/pylintrc
entertainer-0.1/src/tools/
entertainer-0.1/src/tools/run_debug.py
entertainer-0.1/src/tools/loc.py
entertainer-0.1/src/entertainer-log-viewer.py
entertainer-0.1/src/utils/
entertainer-0.1/src/utils/logger.py
entertainer-0.1/src/utils/feed_utils.py
entertainer-0.1/src/utils/image_thumbnailer.py
entertainer-0.1/src/utils/weather.py
entertainer-0.1/src/utils/thumbnailer.py
entertainer-0.1/src/utils/albumart_downloader.py
entertainer-0.1/src/utils/video_thumbnailer.py
entertainer-0.1/src/utils/system_tray_icon.py
entertainer-0.1/src/utils/cd_utils.py
entertainer-0.1/src/utils/content_management_dialog.py
entertainer-0.1/src/utils/log_viewer.py
entertainer-0.1/src/utils/theme.py
entertainer-0.1/src/utils/glade/
entertainer-0.1/src/utils/glade/entertainer-preferences.glade
entertainer-0.1/src/utils/glade/system_tray_icon_menu.glade
entertainer-0.1/src/utils/glade/entertainer-content-management.glade
entertainer-0.1/src/utils/glade/open_feed_source_dialog.glade
entertainer-0.1/src/utils/glade/log_dialog.glade
entertainer-0.1/src/utils/glade/resolve_conflict_dialog.glade
entertainer-0.1/src/utils/__init__.py
entertainer-0.1/src/utils/lyrics_downloader.py
entertainer-0.1/src/utils/preferences_dialog.py
entertainer-0.1/src/utils/open_feed_source_dialog.py
entertainer-0.1/src/utils/resolve_dialog.py
entertainer-0.1/src/utils/EXIF.py
entertainer-0.1/src/utils/configuration.py
entertainer-0.1/src/entertainer-messagebus-notifier.py
entertainer-0.1/src/entertainer-content-management.py
entertainer-0.1/src/entertainer-preferences.py
entertainer-0.1/src/__init__.py
entertainer-0.1/src/tests/
entertainer-0.1/src/tests/Logger_test.py
entertainer-0.1/src/tests/FrontendFeedEntry_test.py
entertainer-0.1/src/tests/SystemTrayMessageHandler_test.py
entertainer-0.1/src/tests/Weather_test.py
entertainer-0.1/src/tests/VideoMetadataSearch_test.py
entertainer-0.1/src/tests/data/
entertainer-0.1/src/tests/data/Weather/
entertainer-0.1/src/tests/data/Weather/forecastrss.xml
entertainer-0.1/src/tests/data/ImageThumbnailer/
entertainer-0.1/src/tests/data/ImageThumbnailer/test.jpg
entertainer-0.1/src/tests/data/VideoThumbnailer/
entertainer-0.1/src/tests/data/VideoThumbnailer/test.flv
entertainer-0.1/src/tests/data/VideoThumbnailer/test.avi
entertainer-0.1/src/tests/data/OPMLParser/
entertainer-0.1/src/tests/data/OPMLParser/lifereaMultiple/
entertainer-0.1/src/tests/data/OPMLParser/lifereaMultiple/.liferea_1.4/
entertainer-0.1/src/tests/data/OPMLParser/lifereaMultiple/.liferea_1.4/feedlist.opml
entertainer-0.1/src/tests/data/OPMLParser/lifereaNoFile/
entertainer-0.1/src/tests/data/OPMLParser/noXML.txt
entertainer-0.1/src/tests/data/OPMLParser/lifereaSingle/
entertainer-0.1/src/tests/data/OPMLParser/lifereaSingle/.liferea/
entertainer-0.1/src/tests/data/OPMLParser/lifereaSingle/.liferea/feedlist.opml
entertainer-0.1/src/tests/data/OPMLParser/opmlInOpml.opml
entertainer-0.1/src/tests/data/OPMLParser/lifereaNoFolder/
entertainer-0.1/src/tests/data/OPMLParser/test.opml
entertainer-0.1/src/tests/data/FeedConfigTools/
entertainer-0.1/src/tests/data/FeedConfigTools/content.conf
entertainer-0.1/src/tests/data/FeedConfigTools/test.opml
entertainer-0.1/src/tests/data/LyricsDownloader/
entertainer-0.1/src/tests/data/LyricsDownloader/lyrics_xml
entertainer-0.1/src/tests/data/LyricsDownloader/final_lyrics
entertainer-0.1/src/tests/OPMLParser_test.py
entertainer-0.1/src/tests/Thumbnailer_test.py
entertainer-0.1/src/tests/Album_test.py
entertainer-0.1/src/tests/Configuration_test.py
entertainer-0.1/src/tests/MusicLibrary_test.py
entertainer-0.1/src/tests/VideoThumbnailer_test.py
entertainer-0.1/src/tests/ImageThumbnailer_test.py
entertainer-0.1/src/tests/LyricsDownloader_test.py
entertainer-0.1/src/tests/FrontendFeed_test.py
entertainer-0.1/src/tests/BackendServer_test.py
entertainer-0.1/src/tests/__init__.py
entertainer-0.1/src/tests/FeedEntryParser_test.py
entertainer-0.1/src/tests/FeedConfigTools_test.py
entertainer-0.1/src/tests/README
entertainer-0.1/src/tests/Track_test.py
entertainer-0.1/src/tests/Music_test.py
entertainer-0.1/src/tests/run_tests.py
entertainer-0.1/src/tests/FrontendFeedLibrary_test.py
entertainer-0.1/src/entertainer-frontend.py
entertainer-0.1/src/frontend/
entertainer-0.1/src/frontend/user_event.py
entertainer-0.1/src/frontend/medialibrary/
entertainer-0.1/src/frontend/medialibrary/playable.py
entertainer-0.1/src/frontend/medialibrary/images.py
entertainer-0.1/src/frontend/medialibrary/playlist.py
entertainer-0.1/src/frontend/medialibrary/videos.py
entertainer-0.1/src/frontend/medialibrary/feeds.py
entertainer-0.1/src/frontend/medialibrary/music.py
entertainer-0.1/src/frontend/medialibrary/__init__.py
entertainer-0.1/src/frontend/backend_connection.py
entertainer-0.1/src/frontend/gui/
entertainer-0.1/src/frontend/gui/tabs/
entertainer-0.1/src/frontend/gui/tabs/movies_tab.py
entertainer-0.1/src/frontend/gui/tabs/series_tab.py
entertainer-0.1/src/frontend/gui/tabs/video_clips_tab.py
entertainer-0.1/src/frontend/gui/tabs/__init__.py
entertainer-0.1/src/frontend/gui/tabs/music_videos_tab.py
entertainer-0.1/src/frontend/gui/tabs/tab.py
entertainer-0.1/src/frontend/gui/screen_history.py
entertainer-0.1/src/frontend/gui/transitions/
entertainer-0.1/src/frontend/gui/transitions/fade_transition.py
entertainer-0.1/src/frontend/gui/transitions/slide_and_fade_transition.py
entertainer-0.1/src/frontend/gui/transitions/zoom_and_fade_transition.py
entertainer-0.1/src/frontend/gui/transitions/no_effect_transition.py
entertainer-0.1/src/frontend/gui/transitions/__init__.py
entertainer-0.1/src/frontend/gui/transitions/transition.py
entertainer-0.1/src/frontend/gui/transitions/slide_transition.py
entertainer-0.1/src/frontend/gui/user_interface.py
entertainer-0.1/src/frontend/gui/frontend_window.py
entertainer-0.1/src/frontend/gui/__init__.py
entertainer-0.1/src/frontend/gui/widgets/
entertainer-0.1/src/frontend/gui/widgets/selector.py
entertainer-0.1/src/frontend/gui/widgets/image_menu_item.py
entertainer-0.1/src/frontend/gui/widgets/scalable_cairo_label.py
entertainer-0.1/src/frontend/gui/widgets/desktop.py
entertainer-0.1/src/frontend/gui/widgets/progress_bar.py
entertainer-0.1/src/frontend/gui/widgets/clock_label.py
entertainer-0.1/src/frontend/gui/widgets/grid_menu.py
entertainer-0.1/src/frontend/gui/widgets/eyecandy_texture.py
entertainer-0.1/src/frontend/gui/widgets/list_indicator.py
entertainer-0.1/src/frontend/gui/widgets/tabs_menu.py
entertainer-0.1/src/frontend/gui/widgets/menu_item.py
entertainer-0.1/src/frontend/gui/widgets/rounded_texture.py
entertainer-0.1/src/frontend/gui/widgets/justified_text_menu_item.py
entertainer-0.1/src/frontend/gui/widgets/menu_overlay.py
entertainer-0.1/src/frontend/gui/widgets/image_menu.py
entertainer-0.1/src/frontend/gui/widgets/arrow_texture.py
entertainer-0.1/src/frontend/gui/widgets/scroll_menu.py
entertainer-0.1/src/frontend/gui/widgets/text_menu_item.py
entertainer-0.1/src/frontend/gui/widgets/loading_animation.py
entertainer-0.1/src/frontend/gui/widgets/__init__.py
entertainer-0.1/src/frontend/gui/widgets/scroll_area.py
entertainer-0.1/src/frontend/gui/widgets/reflection_texture.py
entertainer-0.1/src/frontend/gui/widgets/menu.py
entertainer-0.1/src/frontend/gui/widgets/text_menu.py
entertainer-0.1/src/frontend/gui/widgets/tab_group.py
entertainer-0.1/src/frontend/gui/screens/
entertainer-0.1/src/frontend/gui/screens/tv_serie_episodes_screen.py
entertainer-0.1/src/frontend/gui/screens/tv_serie_screen.py
entertainer-0.1/src/frontend/gui/screens/video_screen.py
entertainer-0.1/src/frontend/gui/screens/photoalbums_screen.py
entertainer-0.1/src/frontend/gui/screens/rss_screen.py
entertainer-0.1/src/frontend/gui/screens/photo_screen.py
entertainer-0.1/src/frontend/gui/screens/tv_osd_screen.py
entertainer-0.1/src/frontend/gui/screens/feed_screen.py
entertainer-0.1/src/frontend/gui/screens/weather_screen.py
entertainer-0.1/src/frontend/gui/screens/video_osd_screen.py
entertainer-0.1/src/frontend/gui/screens/movie_screen.py
entertainer-0.1/src/frontend/gui/screens/feed_entry_screen.py
entertainer-0.1/src/frontend/gui/screens/disc_screen.py
entertainer-0.1/src/frontend/gui/screens/photographs_screen.py
entertainer-0.1/src/frontend/gui/screens/audio_play_screen.py
entertainer-0.1/src/frontend/gui/screens/artist_screen.py
entertainer-0.1/src/frontend/gui/screens/__init__.py
entertainer-0.1/src/frontend/gui/screens/music_screen.py
entertainer-0.1/src/frontend/gui/screens/screen.py
entertainer-0.1/src/frontend/gui/screens/question_dialog.py
entertainer-0.1/src/frontend/gui/screens/main_screen.py
entertainer-0.1/src/frontend/gui/screens/album_screen.py
entertainer-0.1/src/frontend/glade/
entertainer-0.1/src/frontend/glade/entertainer-window.glade
entertainer-0.1/src/frontend/__init__.py
entertainer-0.1/src/frontend/media_player.py
entertainer-0.1/src/frontend/frontend_client.py
entertainer-0.1/src/Makefile
entertainer-0.1/src/entertainer-backend.py
entertainer-0.1/src/backend/
entertainer-0.1/src/backend/core/
entertainer-0.1/src/backend/core/message_scheduler.py
entertainer-0.1/src/backend/core/message_type_priority.py
entertainer-0.1/src/backend/core/message_bus.py
entertainer-0.1/src/backend/core/message_generator.py
entertainer-0.1/src/backend/core/message_bus_proxy.py
entertainer-0.1/src/backend/core/message.py
entertainer-0.1/src/backend/core/__init__.py
entertainer-0.1/src/backend/core/connection_server.py
entertainer-0.1/src/backend/core/message_handler.py
entertainer-0.1/src/backend/core/client_connection.py
entertainer-0.1/src/backend/components/
entertainer-0.1/src/backend/components/weather/
entertainer-0.1/src/backend/components/weather/weather_fetcher.py
entertainer-0.1/src/backend/components/weather/weather_manager.py
entertainer-0.1/src/backend/components/weather/__init__.py
entertainer-0.1/src/backend/components/tvguide/
entertainer-0.1/src/backend/components/tvguide/__init__.py
entertainer-0.1/src/backend/components/tvguide/guide_updater.py
entertainer-0.1/src/backend/components/feeds/
entertainer-0.1/src/backend/components/feeds/feed_fetcher.py
entertainer-0.1/src/backend/components/feeds/feed_manager.py
entertainer-0.1/src/backend/components/feeds/__init__.py
entertainer-0.1/src/backend/components/mediacache/
entertainer-0.1/src/backend/components/mediacache/video_metadata_search.py
entertainer-0.1/src/backend/components/mediacache/file_system_observer.py
entertainer-0.1/src/backend/components/mediacache/cache.py
entertainer-0.1/src/backend/components/mediacache/video_cache.py
entertainer-0.1/src/backend/components/mediacache/indexer_thread.py
entertainer-0.1/src/backend/components/mediacache/video_cache_inotify_handler.py
entertainer-0.1/src/backend/components/mediacache/image_cache_inotify_handler.py
entertainer-0.1/src/backend/components/mediacache/music_cache.py
entertainer-0.1/src/backend/components/mediacache/music_cache_inotify_handler.py
entertainer-0.1/src/backend/components/mediacache/media_cache_manager.py
entertainer-0.1/src/backend/components/mediacache/__init__.py
entertainer-0.1/src/backend/components/mediacache/image_cache.py
entertainer-0.1/src/backend/components/__init__.py
entertainer-0.1/src/backend/__init__.py
entertainer-0.1/src/backend/backend_server.py
entertainer-0.1/README
entertainer-0.1/TODO
entertainer-0.1/EXIF_LICENCE
chris@awesometop:~/Source$ cd entertainer-0.1
chris@awesometop:~/Source/entertainer-0.1$ ./configure
bash: ./configure: No such file or directory
```

(I have a folder in my home directory called source, which I use for all the tar files, ect. that download and extract.)

What am I doing wrong? What needs to be done?

---

### Post by snova on 2008-10-18
It's Python. The source *is* the binary, therefore no compilation is necessary. You're not doing anything wrong, the instructions are simply inappropriate to this particular program.

Read the files included in it for instructions, as the normal method by which Python programs are usually installed does not appear to be present. Check the README first.

---

### Post by opothehippo on 2008-10-18
The readme says this:

```
 ENTERTAINER - Media Center application
 -------------------------------------------------------------------------------
 Entertainer is a basic Media Center application that allows you to browse your
 media easily with remote control. It is intended to be used on a computer that
 is dedicated to be a media center, but it's not required and you can use it on
 your desktop computer as well.

 Directory hierarcy
 -------------------------------------------------------------------------------
 cfg			 - Config file templates (default configuration)
			   copy all files and dirs under ~/.entertainer
	
 docs			 - ENTERTAINER documentation
    notes		 - Misc. notes about this project
    diagrams		 - Design diagrams (PNG & DIA)
       backend		 - Backend specific diagrams
       frontend		 - Frontend sepcific diagrams
       ER		 - ER-diagrams (cache structures)
 
 src			 - ENTERTAINER source code
    backend		 - Server side code
       core		 - Server core: messagebus
       components	 - Server side components
    frontend		 - Frontend code
       medialibrary	 - Media library source files
       gui	  	 - GUI specific source files
       glade		 - Glade file of the frontend application
    extra-tools		 - Extra tools: preferences dialog etc.
       glade		 - Glade files (GUI) of the extra tools
    utils		 - Misc util classes
```


Which to me doesnt mean much. How would I install entertainer now that I know its not going to work normaly?

Spoonfed would help.

---

### Post by mc4man on 2008-10-18
Read here - 3rd post from bottom
[https://answers.launchpad.net/entertainer/+question/39028/+index](https://answers.launchpad.net/entertainer/+question/39028/+index)

[http://code.google.com/p/entertainer-media-center/wiki/Key_bindings](http://code.google.com/p/entertainer-media-center/wiki/Key_bindings)

---

### Post by opothehippo on 2008-10-18
Super Awesome, I got it working now. I dont know how I didnt find that before.

---

