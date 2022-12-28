from lxml import html
import datetime
def scrapChannels(fileLocation):
    with open(fileLocation,"r", encoding="utf8") as f:
        page = f.read()
    tree = html.fromstring(page)
    channels = tree.xpath(
        '//div[@class="content-cell mdl-cell mdl-cell--6-col mdl-typography--body-1"]/a[2]/text()')
    return channels

def scrapDates(fileLocation):
    with open(fileLocation,"r", encoding="utf8") as f:
        page = f.read()
    tree = html.fromstring(page)
    dates = tree.xpath(
        '//div[@class="content-cell mdl-cell mdl-cell--6-col mdl-typography--body-1"]/text()')
    return dates

def qFromAChannel(channels):
    channel = input("Enter channel: ")
    print("The amount of videos watched from the channel " + channel + " is: " + str(channels.count(channel)))

def qFromADate(dates):
    dateInput = input("Enter date (DD/MM/YYYY): ")
    dateSeparated = dateInput.split("/")
    date = datetime.date(int(dateSeparated[2]), int(dateSeparated[1]), int(dateSeparated[0]))
    # Dec 22, 2022
    searchableDate = date.strftime("%b") + " " + date.strftime("%d") + ", " + date.strftime("%Y") 
    matching = [s for s in dates if searchableDate in s]
    print("The amount of videos watched on " + searchableDate + " was: " + str(len(matching)))

def top10(channels):
    dict = {}
    for channel in channels:
        # print("Videos watched from " + channel + ": " + str(channels.count(channel)))
        if channel in dict.keys():
            continue
        dict[channel] = channels.count(channel)
    
    sortedItems = sorted(dict.items(), key=lambda x:x[1], reverse=True)
    first_ten = list(sortedItems)[:10]
    for idx, item in enumerate(first_ten):
        print(idx + 1, item[0] + ": " + str(item[1]))

    

def main():
    file = input("Enter location of watch history file: ")
    channels = scrapChannels(file)
    dates = scrapDates(file)
    while True:
        print("A. Number of videos watched from one channel")
        print("B. Number of videos watched a specific date")
        print("C. Top 10 channels")
        option = input("Enter an option: ")
        if option == "A":
            qFromAChannel(channels)
        elif option == "B":
            qFromADate(dates)
        elif option == "C":
            top10(channels)


main()