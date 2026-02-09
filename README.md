# meow
type Hobby = "cooking" | "drawing" | "singing" | "dancing"
type Extra = "english" | "math" | "PE" | "biology"
type Facultative = Hobby | Extra

let hobby1: Hobby;
hobby1 = "cooking"
hobby1 = "dancing"
hobby1 = "traveling"

let extra1: Extra;
extra1 = "biology"
extra1 = "geography"
extra1 = "PE"

type Student = { 
    name: string
    age: Age
    group: Group
    facultative: Facultative
}

let stud1: Student = {
    name: "Sasha",
    age: 19,
    group: "A",
    facultative: "cooking"
}

let stud2 : Student = {
    name: "Lera",
    age: 17,
    group: "D",
    facultative: "dancing"
}

interface StudentI {
    name: string
    age: Age
    group: Group
    facultative: Facultative
}

let studI1: StudentI = {
    name: "Mla",
    age: 18,
    group: "C",
    facultative: "PE"
}

let studI2 : StudentI = {
    name: "Manunya",
    age: 25,
    group: "A",
    facultative: "biology"
}
// на данном этапе я не заметила особой разницы, только знак равно перед фигурной скобкой в type

type Age = 17 | 18 | 19 | 20
type Group = "A" | "B" | "C"

class StudentClass {
    name: string
    age: Age
    group: Group
    facultative: Facultative

    constructor(name: string, age: Age, group: Group, facultative: Facultative) {
        this.name = name
        this.age = age
        this.group = group
        this.facultative = facultative
    }

    info(): string {
        return `${this.name}, ${this.age}, ${this.group}, ${this.facultative}`
    }
}

const liza = new StudentClass ("Liza", 17, "C", "dancing")
const ivan = new StudentClass ("Ivan", 20, "B", "math")

console.log(liza.info(), ivan.info())

class School {
    students: StudentClass[] = []

    addStudent (student: StudentClass) {
        this.students.push(student)
    }

    listNames() : string[] {
        return this.students.map(student => student.name)
    }

    countByFacultative(f: Facultative): number {
        return this.students.filter( student => student.facultative === f).length
    }
}

const school = new School()
school.addStudent(ivan)
school.addStudent(liza)
school.addStudent(new StudentClass("Vika", 19, "A", "math"))

const names: string[] = school.listNames()
console.log(names)

const countMath = school.countByFacultative("math")
console.log(`Math: ${countMath}`)

