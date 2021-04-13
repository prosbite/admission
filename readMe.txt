Installation Instruction

1. Rename server/src/app/Envs.sling to Env.sling
2. Rename client/src/app/Envs.sling to Env.sling
4. Open Env files and edit the ports accordingly
5. run the following queries inside mysql sms_db

CREATE VIEW admission_student as 
SELECT
student.firstname,
student.middlename,
student.gender,
student.lastname,
student.student_id,
student.created_at,
student.updated_at
FROM
student
WHERE
student.student_id NOT IN (SELECT student_id FROM admission)

CREATE VIEW admitted_students as 
SELECT
admission.adm_id,
admission.student_id,
admission.course,
admission.sy,
admission.sem,
admission.created_at,
admission.updated_at,
student.firstname,
student.middlename,
student.lastname,
student.gender
FROM
admission
INNER JOIN student ON admission.student_id = student.student_id

6. Default username/password is admin/admin

7. Done