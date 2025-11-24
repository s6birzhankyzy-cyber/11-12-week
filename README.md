# 11-12-week
11 week
class Task:
    def __init__(self, title, deadline, priority):
        self.title = title
        self.deadline = deadline
        self.priority = priority

    def show_info(self):
        print(f"Тапсырма: {self.title}")
        print(f"Дедлайн: {self.deadline}")
        print(f"Маңыздылығы: {self.priority}")
        print("----------------------------")


class Schedule:
    def __init__(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append(task)
        print(f"'{task.title}' тапсырмасы қосылды.")

    def show_all_tasks(self):
        print("\nЖоспардағы тапсырмалар:")
        if not self.tasks:
            print("Тапсырма жоқ.")
        for task in self.tasks:
            task.show_info()


class User:
    def __init__(self, name):
        self.name = name

    def show_user(self):
        print(f"Қолданушы: {self.name}")


class Admin(User):
    def __init__(self, name):
        super().__init__(name)

    def delete_task(self, schedule, title):
        for task in schedule.tasks:
            if task.title == title:
                schedule.tasks.remove(task)
                print(f"Админ '{title}' тапсырмасын өшірді.")
                return
        print("Ондай тапсырма табылмады.")


t1 = Task("Теория оқу", "2025-01-10", "High")
t2 = Task("Жаттығу жасау", "2025-01-11", "Medium")
t3 = Task("Ұйқы режимін реттеу", "2025-01-12", "Low")

schedule = Schedule()
schedule.add_task(t1)
schedule.add_task(t2)
schedule.add_task(t3)

user = User("Сезім")
user.show_user()

admin = Admin("Нұрай")
admin.show_user()

schedule.show_all_tasks()

admin.delete_task(schedule, "Жаттығу жасау")

schedule.show_all_tasks()
