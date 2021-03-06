include ../../extra.mk

PROG = audacious${PROG_SUFFIX}
SRCS = adder.c \
       art.c \
       chardet.c								\
       config.c \
       drct.c \
       effect.c									\
       equalizer.c								\
       equalizer_preset.c						\
       fft.c									\
       general.c \
       history.c \
       interface.c								\
       main.c									\
       output.c									\
       playback.c								\
       playlist-files.c \
       playlist-new.c \
       playlist-utils.c \
       pluginenum.c								\
       plugin-preferences.c \
       plugin-registry.c \
       plugin-init.c \
       plugin-view.c \
       probe.c \
       probe-buffer.c \
       scanner.c \
       signals.c								\
       ui_plugin_menu.c \
       ui_preferences.c							\
       util.c									\
       vis_runner.c \
       visualization.c							\
       ui_albumart.c

ifeq ($(HAVE_MSWINDOWS),yes)
SRCS += audacious.rc
endif

INCLUDES = api.h \
           api-alias-begin.h \
           api-alias-end.h \
           api-define-begin.h \
           api-define-end.h \
           debug.h \
           drct.h \
           drct-api.h \
           i18n.h				\
           misc.h \
           misc-api.h \
           playlist.h \
           playlist-api.h \
           plugin.h				\
           plugins.h \
           plugins-api.h \
           preferences.h		\
           types.h

DATA = images/about-logo.png				\
       images/album.png \
       images/audacious.png \
       images/audio.png						\
       images/connectivity.png				\
       images/info.png \
       images/menu_playlist.png				\
       images/menu_plugin.png				\
       images/menu_queue_toggle.png			\
       images/playlist.png					\
       images/plugins.png

CLEAN = build_stamp.c

ifeq ($(USE_DBUS),yes)
SRCS += dbus-server.c
EXT_DEPS += ../dbus/aud-dbus.a
endif

include ../../buildsys.mk

ifeq ($(USE_DBUS),yes)
CPPFLAGS := -I../dbus ${CPPFLAGS} ${GIO_UNIX_CFLAGS}
LIBS := ../dbus/aud-dbus.a ${LIBS} ${GIO_UNIX_LIBS}
endif

CPPFLAGS := -I.. -I../.. \
            ${CPPFLAGS} \
		${GLIB_CFLAGS}			\
		${GMODULE_CFLAGS} \
		${GTK_CFLAGS}			\
		${AUDACIOUS_DEFINES}	\
		${REGEX_CFLAGS}			\
		-D_AUDACIOUS_CORE		\
		${LIBGUESS_CFLAGS}

LIBS := -L../libaudcore -laudcore \
        -L../libaudgui -laudgui \
        -L../libaudtag -laudtag \
        ${LIBS} -lm \
		${LIBINTL}						\
		${GLIB_LIBS}					\
		${GMODULE_LIBS} \
		${GTK_LIBS}						\
		${REGEX_LIBS}					\
		${LIBGUESS_LIBS}

desktop_DATA = audacious.desktop
desktopdir = ${datarootdir}/applications
