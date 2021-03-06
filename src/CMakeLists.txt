INCLUDE_DIRECTORIES( ${CMAKE_BINARY_DIR}/src )

# Project files
SET( kchmviewerSources 
	config.cpp
	dbus_interface.cpp
	dialog_chooseurlfromlist.cpp
	dialog_setup.cpp
	kde-qt.cpp
	main.cpp
	mainwindow.cpp
	recentfiles.cpp
	settings.cpp
	tab_bookmarks.cpp
	tab_contents.cpp
	tab_index.cpp
	tab_search.cpp
	viewwindow.cpp
	viewwindowmgr.cpp
	navigationpanel.cpp
	checknewversion.cpp
	toolbarmanager.cpp
	toolbareditor.cpp
	qwebviewnetwork.cpp
	textencodings.cpp
	treeitem_toc.cpp
	treeitem_index.cpp
  )

# UI files
KDE4_ADD_UI_FILES( kchmviewerSources 
	dialog_about.ui
	dialog_setup.ui
	dialog_topicselector.ui
	mainwindow.ui
	navigatorpanel.ui
	tab_bookmarks.ui
	tab_contents.ui
	tab_index.ui
	tab_search.ui
	toolbareditor.ui
	window_browser.ui
   )

# Resources
QT4_ADD_RESOURCES( kchmviewerResources resources/images.qrc )

KDE4_ADD_EXECUTABLE( kchmviewer ${kchmviewerSources} ${kchmviewerResources} )

TARGET_LINK_LIBRARIES( kchmviewer 
	ebook
	${LIBCHM_LIBRARY}
	${LIBZIP_LIBRARY}
	${KDE4_KDEUI_LIBS} 
	${QT_QTWEBKIT_LIBRARY}	
	${KDE4_KFILE_LIBS}  )

INSTALL( TARGETS kchmviewer DESTINATION ${KDE4_BIN_INSTALL_DIR} )

