#!/usr/bin/python

from pyquery import PyQuery as pq
from lxml import etree
import requests
from bs4 import BeautifulSoup
import time
import numpy as np

def WriteArtistLyrics(artist,popular=False):
	# this visits the website
	if popular is False:
		artistVersesWritten=0;
		print "#####FETCHING LYRICS BY ARTIST: {}########".format(artist)
		artistUrl='http://www.metrolyrics.com/{}-lyrics.html'.format(artist)
		print 'Using Url:' + artistUrl
		response = requests.get(artistUrl)
		myfile = open('/home/soren/Documents/RapperAI/MetroLyrics1.txt','a')
		# this separates the different types of content
		doc = pq(response.content)

		# this finds the titles in the content
		titles = doc('.title')

		# this visits each title, then prints each verse
		for title in titles:
		    # this visits each title
		  #response_title = requests.get(title)
		  time.sleep(np.random.random()+0.5)
		  response_title = requests.get(title.attrib['href'])

		    # this separates the content
		  doc2 = pq(response_title.content)
		    # this finds the song lyrics
		  verse = doc2('.verse')

		    # this prints the song lyrics
		  #print verse.text()
		  verseW = str(verse)
		  verseW=verseW.replace('<br/>','')
		  verseW=verseW.replace('<p class="verse">','')
		  verseW=verseW.replace('</p>','')
		  if verseW is not None:
		  	artistVersesWritten+=1
		  myfile.write(verseW)
		
		#for i in range(3):
		#	print('##########################################################')
		print 'got {} verses from artist {}'.format(
			artistVersesWritten,
			artist
			)
		#for i in range(3):
		#	print('##########################################################')
		return artistVersesWritten
	#else if popular is True:

popularArtists=['drake','kanye-west','kendrick-lamar',
	'jay-z','2pac','asap-rocky','lil-wayne']
artistList=[
	'drake','kanye-west','kendrick-lamar',
	'jay-z','2pac','asap-rocky','action-bronson',
	'50-cent','talib-kweli','jay-electronica',
	'jay-rock','asap-ferg','eminem','andre-3000','busta-rhymes','mos-def','method-man',
	'j-cole','big-sean','pusha-t','ice-cube','krs-one',
	'outkast','common','ludacris','big-daddy-kane',
	'lil-wayne','ghostface-killah','big-boi','rakim',
	'notorious-big','snoop-dogg','joey-badass','nate-dogg',
	'rza','the-game','xzibit','warren-g','mf-doom','kid-cudi',
	'twista','tyga','fetty-wap','jadakiss','grandmaster-flash',
	'raekwon','kurupt','dr-dre','wiz-khalifa','chance-the-rapper',
	'too-short','e-40','fabolous','ice-t','young-thug','migos',
	'childish-gambino','eazy-e','ll-cool-j','dreezy','coolio',
	'g-eazy','bob','flo-rida','soulja-boy','t-pain','macklemore',
	'mc-hammer','beastie-boys','logic','earl-sweatshirt',
	'tyler-the-creator','mac-miller','wale','hopsin','yg',
	'travis-scott','kid-ink','vic-mensa','vince-staples',
	'ab-soul','dizzy-wright','mgk','isaiah-rashad','flatbush-zombies',
	'mick-jenkins','kevin-gates','big-pun','rae-sremmurd',
	'casey-veggies','yelawolf','rich-homie-quan','the-weeknd',
	'chief-keef','juicy-j','denzel-curry','danny-brown',
	'freddie-gibbs','underachievers','run-the-jewels','lupe-fiasco',
	'lil-herb','bishop-nehru','lil-b','post-malone','cypress-hill',
	'macklemore-ryan-lewis','wu-tang-clan','a-tribe-called-quest',
	'aesop-rock','brother-ali','atmosphere','pimp-c','heavy-d',
	'meek-mill','big-krit','nwa','redman','public-enemy',
	'immortal-technique','scarface','slick-rick','q-tip',
	'master-p','mobb-deep','2-chainz','tech-n9ne','young-jeezy',
	'gucci-mane','ol-dirty-bastard','the-roots','de-la-soul',
	'public-enemy','rick-ross','lil-jon','yung-lean','yung-joc',	
	'nipsey hussle','royce-da-59','i-love-makonnen','fat-joe','murs',
	'the-pharcyde','hilltop-hoods','eyedea','madvillain','canibus',
	'alchemist','asap-mob','afrika-bambaataa','dead-prez','french-montana',
	'yo-gotti',	'bj-chicago-kid',	'max-b','dej-loaf','quavo','odd-future',
	'machine-gun-kelly','spaceghostpurp','theophilius-london',
	'bobby-shmurda','puff-daddy','lil-boosie','lil-yachty','lil-durk',
	'yung-simmie','young dro','young scooter','clipse','no malice',
	'lil scrappy','kool-g-rap','chamillionaire','blueprint',
	'bone-thugs-n-harmony','slim-thug','kanye-west-and-jay-z',
	'sage-the-gemini','el-p','killer-mike','pac-div','ace-hood',
	'ty-dolla-sign','jeremih','diddy','p-diddy','rich-gang','epmd',
	'nicki-minaj','del-the-funky-homosapien','deltron-3030',
	'hieroglyphics','lil-bow-wow','boyz-n-da-hood','hoodie-allen','gza',
	'schoolboy-q','nas',
	'dmx'
	]
totalverses=0
for artist in artistList:
	totalverses+=WriteArtistLyrics(artist)
	print('sleeping for a random amount of time so metrolyrics doesnt ban me')
	time.sleep(np.random.random()*1.5)
print "TOTAL VERSES: {}| NUMBER OF ARTISTS: {}".format(totalverses,len(artistList))
